# 4d-plugin-mac-color-picker
Alternative color picker for 4D on Mac.

Note
---
Consider using the native command and [convert-color-space](https://github.com/miyako/4d-plugin-convert-color-space) to convert the RGB values. Running ```NSColorPanel``` from a plugin has some modality issues.

About
---
You might have noticed that if you pass the RGB value returned from the built-in [Select RGB color](http://doc.4d.com/4Dv15/4D/15/Select-RGB-Color.301-2007529.en.html) command directly to [OBJECT SET RGB COLORS](http://doc.4d.com/4Dv15/4D/15/OBJECT-SET-RGB-COLORS.301-2006928.en.html), you get a slightly **darker** colour.

![](https://github.com/miyako/4d-plugin-mac-color-picker/blob/master/images/picker.png)

For example, the standard window background colour is ```#E7E7E7```.

However, if you pass this value to a form object, or even reference it in SVG, it is rendered slightly darker on an LCD.

![](https://github.com/miyako/4d-plugin-mac-color-picker/blob/master/images/result.png)

Apparently the RGB value must be calibrated for the device colour space.

c.f. http://stackoverflow.com/questions/14578759/wrong-color-in-interface-builder

This plugin returns the exact RGB needed on screen, if you pass ```Picker standard color space```.

The aforementioned ```#E7E7E7``` is converted to ```#ECECEC```.

![](https://github.com/miyako/4d-plugin-mac-color-picker/blob/master/images/plugin.png)

In addition, it lets you displayed the alpha channel tool if you pass ```Picker RGBA color```.

The alpha value is returned in the most significant byte, currently not used in 4D.

![](https://github.com/miyako/4d-plugin-mac-color-picker/blob/master/images/alpha.png)

Finally, the crayon tool, which displays wrongly on El Capitan + 4D 32 bits, is hidden.

Remarks
---
~~The calibrartion is not perfect; in the above example, the window background should be ```#ECECEC```.~~

The conversion is OK but the panel is not modal to the window that invoked it.
