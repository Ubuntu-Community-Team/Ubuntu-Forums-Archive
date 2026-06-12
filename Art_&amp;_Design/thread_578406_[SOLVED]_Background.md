---
title: "[SOLVED] Background"
date: 2007-10-17
forum: Art &amp; Design
---

### Post by Roque2 on 2007-10-17
okay maybe I should have posted in here first. Okay I am having a problem in Gutsy finding where I can change the background color when natulis is logging on . I have a login manager that loads with a different color background but when the nautilis screen loads with my splash design its tan with like my blue splash design. makes it look stupid. Could anyone show me or tell me how in Gutsy to remove that tan background. Pls Pls Pls

---

### Post by bigken on 2007-10-17
system/preferences/apperance

click the background tab and select the desired colour

---

### Post by bigken on 2007-10-17
sorry thats not it hmmmmmm :confused:

---

### Post by Roque2 on 2007-10-17
nope. I had it changed before I updated with Gutsy. Think Gutsy is hiding it

---

### Post by psmar on 2007-10-17
try system preferences login window (its the gdm interface I believe the color choice there will run threw the startup windows

---

### Post by Hairy_Palms on 2007-10-17
this has been around since about tribe 3, theres a post somewhere that tells you how to get around it by editting a hardcoded value, try searching around a bit.

---

### Post by exploder on 2007-10-17
Here you go!

Fix Logon background color


Here's how you can change it manually:
Code:
sudo gedit /etc/gdm/PreSession/Default
Then look for
Code:
        # Default value
        if [ "x$BACKCOLOR" = "x" ]; then
                BACKCOLOR="#dab082"
And change the hexadecimal code to whichever you like.
E.g. for black #000000 and white #FFFFFF

Now all you need to do is figure out the hexadecimal code for blue.

I saved this fix from another post.

---

### Post by Roque2 on 2007-10-18
Worked like a charm, thank you so very very much

---

### Post by exploder on 2007-10-19
You are welcome. Glad you got it fixed!

---

### Post by twrock on 2007-10-19
Yes, thanks for that fix.
I do think that this is one of those "simple" things they should incorporate into System>Preferences>Appearance though. Didn't it used to be controlled by the GDM background color? Why not still have that as the control even if they killed the splash screen? (Either that or control it via the desktop background color.)

For future reference, getting the color hex code to match the GDM background can be done as follows:
System>Administration>Login window
Local tab
Background color button
Copy the color name

---

### Post by Roque2 on 2007-10-21
I got the login color to match my splash screen I need the fix that was just given to make the background after login to match.looked stupid with 2 different colors

---

### Post by Neobuntu on 2007-11-13
Thank you for the solution.

This is very wrong, that we have to hack a configuration script file! This should be users selectable.

---

### Post by por100pre1 on 2007-11-13
> **Neobuntu said:**
> Thank you for the solution.

This is very wrong, that we have to hack a configuration script file! This should be users selectable.

Actually that is not the normal behavior. It is a bug in Gutsy.

---

### Post by Hairy_Palms on 2007-11-14
where it has a hex value should be 'x' instead, that way it follows the gdm setting.

---

### Post by twrock on 2007-11-14
Really? That simple? Can you paste the entire line so I can be sure I am understanding? (I'm one of those Linux noobs who can some times figure out a way, but it isn't often the best way.)

---

### Post by twrock on 2007-11-17
As Hairy_Palms said above, changing the value to "x" solves the problem and sets the background color to whatever the GDM login screen background is. Here is what my Default configuration file looks like:
> # Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="x"

So just change whatever the orginal hex code was to "x".

---

