# PDX Hackerspace Prusa Printer Signs

This is a simple OpenSCAD project that generates STL for a sign with a printer's name and a QR code for the printer's Octoprint controller.

This is a very basic OpenSCAD program. Its interesting parts are raised text, a QR code, and doing a color change for the text (which is trivially done by PrusaSlicer).

## Usage

1. Download and install [OpenSCAD](https://openscad.org) if you haven't already.

2. Edit ctrlh-prusa-signs.scad from this repo and uncomment (remove the `//` from the start of the line) one of:
```
// base();
// printer_sign("Prusa 1", prusa1_qr_data);
// printer_sign("Prusa 2", prusa2_qr_data);
```

Depending on whether you want to print the sign's base or the actual sign for Prusa 1 or Prusa 2.

3. Generate and save the STL file with OpenSCAD.

4. Open the STL file with PrusaSlicer or whatever slicer software you use.

5. Choose the necessary filament and print options and generate the `.GCODE` file.

6. Upload the `.GCODE` file and print it!

Note that PrusaSlicer may warn that there are open edges in the model - these are artifacts from the QR code. In our case it automatically repaired them and everything worked with no actual problems.

## Customizing

Change the the width or the depth of the sign by changing the `width` and `depth` variables in `ctrlh-prusa-signs.scad`.

Change the name of the printer by changing the name in the call to `printer_sign()` in `ctrlh-prusa-signs.scad`.

Change the QR code by generating a new QR code at https://ridercz.github.io/OpenSCAD-QR/, pasting its code into `ctrlh-prusa-signs.scad` and passing its variable name in the call to `printer_sign()` in `ctrlh-prusa-signs.scad`.


## Using Multiple Filament Colors

PrusaSlicer automatically detects the presence of text and offers to insert filament change GCODE in the output.

If you'd like the text and QR code to use a different color filament, just accept this option. You should probably do this so that the QR code is a different color from the background, making it more likely to scan properly.

 A Prusa printer will start beeping when it's time to change the filament and will walk you through unloading and reloading the filamant and automatically resume the print. We would recommend being attentive and not letting the printer sit in this mode for too long. We found that it added a second filament change just before the end of the text and QR code printing - canceling the print at this point is fine unless you really want to change the filament again for the top layer.

## Printing

PLA or PETG would be good filament choices though it's tough to go wrong here.

QR codes work best when there's a high contrast between the elements - black for the print and white for the background is the norm.

We printed at the base and sign at 10% infill, no brim or supports, with no problems.
