# OpenStreetMap Öffnungszeiten-Editor

Die OpenStreetMap Öffnungszeitenspezifikation ist ziemlich komplex und eignet sich nicht ohne weiteres für eine einfache und intuitive Benutzeroberfläche.

However most of the time you will likely only be using a small part of the definition. The editor takes this in to account by trying to hide the more obscure features in menus and most of the time reducing the "on the road" use to small customizations of pre-defined templates.

_Diese Dokumentation ist vorläufig und eine laufende Arbeit_

## Verwenden des Editors für die Öffnungszeiten

In a typical workflow the object you are editing will either already have an opening hours tag (opening_hours, service_times and collection_times) or you can re-apply the preset for the object to get an empty opening hours field. If you need to add the field manually and you are using Vespucci you can enter the key on the details page and then switch back to the form based tab to edit. If you believe that the opening hours tag should have been part of the preset, please open an issue for your editor.

If you have defined a default template (do this via the "Manage templates" menu item) it will be loaded automatically when the editor is started with an empty value. With the "Load template" function you can load any saved template and with the "Save template" menu you can save the current value as a template. You can define separate templates and defaults for the "opening_hours", "collection_times" and "service_times" tags. 

Naturally you can build an opening hours value from scratch, but we would recommend using one of the existing templates as a starting point.

If an existing opening hours value is loaded, an attempt is made to auto-correct it to conform to the opening hours specification. If that is not possible the rough location where the error occurred will be highlighted in the display of the raw OH value and you can try and correct it manually. Roughly a quarter of the OH values in the OpenStreetMap database have problems, but less than 10% can't be corrected, see [OpeningHoursParser](https://github.com/simonpoole/OpeningHoursParser) for more information on what deviations from the specification are tolerated.

### Hauptmenü-Schaltfläche

* __Regel hinzufügen__: eine neue Regel hinzufügen.
* __Add rule for holidays__: add a new rule for a holiday together with a state change.
* __Add rule for 24/7__: add a rule for an object that is always open, the opening hours specification doesn't support any other sub values for 24/7 however we do allow adding of higher level selectors (for example year ranges).
* __Vorlage laden__: eine Vorlage laden.
* __Save to template__: save the current opening hours value as a template for future use.
* __Manage template__: edit, for example change the name, and delete existing templates.
* __Refresh__: re-parse the opening hour value.

### Regeln

Default rules are added as _normal_ rules, this implies that they will override the values of previous rules for the same days. This can be a concern when specifying extended times, typically you will then want to switch the rules via the _Show rule type_ menu entry to _additive_.

#### Regelmenü

* __Add modifier/comment__: change the effect of this rule and add an optional comment.
* __Add holiday__: add a selector for public or school holidays.
* __Zeitspanne hinzufügen...__
    * __Time - time__: a start time to an end time on the same day.
    * __Time - extended time__: a start time to an end time on the next day (example 26:00 is 02:00 (am) the next day.
    * __Var. time - time__: from a start variable time (dawn, dusk, sunrise and sundown) to an end time on the same day.
    * __Var. time - extended time__: from a start variable time to an end time on the next day.
    * __Time - var. time__: a start time to an end variable time.
    * __Var. time - var. time__: a start variable time to an end variable time.
    * __Time__: a point in time.
    * __Time-open end__: from a start point in time onwards.
    * __Variable time__: at the variable time
    * __Variable time-open end__: from a start variable time onwards
* __Add week day range__: add a weekday based selector.
* __Datumsbereich hinzufügen...__
    * __Date - date__: from a start date (year, month, day) to an end date.
    * __Variable date - date__: from a start variable date (currently the specification only defines _easter_) to an end date.
    * __Date - variable date__: from a start date to a variable date.
    * __Variable date - variable date__: from a start variable date to an end variable date.
    * __Occurrence in month - occurrence in month__: from a start weekday occurrence in a month to the same.
    * __Occurrence in month - date__: from a start weekday occurrence in a month to a end date.
    * __Date - occurrence in month__: from a start date to an end weekday occurrence in a month.
    * __Occurrence in month - variable date__: from a start weekday occurrence in a month to an end variable date.
    * __Variable date - occurrence in month__: from a start variable date to an end weekday occurrence in a month.
    * __Date - open end__: from a start date onwards,
    * __Variable date - open end__: from a start variable date onwards.
    * __Occurrence in month - open end__: from a start weekday occurrence in a month onwards.
    * __With offsets...__: the same entries as above however with offsets specified (this is rarely used).
* __Add year range__: add a year based selector.
* __Add week range__: add a week number based selector.
* __Show rule type__: display and allow changing of the rule type _normal_, _additive_ and _fallback_ (not available on the first rule).
* __Move up__: move this rule up one position (not available on the first rule).
* __Move down__: move this rule down one position.
* __Löschen__: diese Regel löschen.

### Zeitspannen

To make editing time spans as easy as possible, we try to choose an optimal time range and granularity for the range bars when loading existing values. For new time spans the bars start at 6:00 (am) and have 15 minute increments, this can be changed via the menu.

#### Zeitspannenmenü

* __Display time picker__: show a large number picker for selecting start and end time, on very small displays this is the preferred way of changing times.
* __Switch to 15 minute ticks__: use 15 minute granularity for the range bar.
* __Switch to 5 minute ticks__: use 5 minute granularity for the range bar.
* __Switch to 1 minute ticks__: use 1 minute granularity for the range bar, very difficult to use on a phone.
* __Start at midnight__: start the range bar at midnight.
* __Intervall anzeigen__: Intervallfeld zum Festlegen eines Intervalls in Minuten anzeigen.
* __Löschen__: diese Zeitspanne löschen.
