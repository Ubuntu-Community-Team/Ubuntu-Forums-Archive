---
title: "sound bios issus"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by jasond123 on 2007-05-27
sound issue. i have a sis soundcard which is detected by ubunty 7 but no sound plays at all. when i plug speakers into onboard sound slots there is all of a sudden sound working!!! i think i need to turn the onboard sound off but dont know how to acces the bios to do it. please help.

---

### Post by kyphi on 2007-05-27
To access the BIOS you need to restart your computer.  When the black screen appears you will see on the top of the screen what kind of video card you have as well as what kind of BIOS.
At the bottom of that same screen it will tell you which button on your keyboard you need to press to access the BIOS.  On some systems this is DEL (delete button) on others it is F2 (there are other variations).

The literature that came with your computer should tell you all that.

When the BIOS screen comes up, scroll with your mouse to 'Integrated Peripherals', then to 'Audio' or 'AC97' and press 'Enter".  On the resulting screen scroll to 'Disable' and press 'Enter' again.

Then press ESC on your keyboard and when the red screen asks 'Save to CMOS and EXIT (Y/N)' press y (for yes).

Then the computer will complete its startup without the inbuilt sound device.

---

