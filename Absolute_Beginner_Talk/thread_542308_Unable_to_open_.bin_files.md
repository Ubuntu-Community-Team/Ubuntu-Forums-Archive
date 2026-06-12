---
title: "Unable to open .bin files"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-09-03
when i try to open any BIN files i get an error that says:

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

when i select Retry with Current Locale (UTF-8 ) or West (ISO-8859-15) it still doesnt work.

---

### Post by taurus on 2007-09-03
You are supposed to run it instead of opening .bin.

Applications -> Accessories -> Terminal
```
chmod 755 filename.bin
./filename.bin
```
What is it anyway?

---

### Post by dianep on 2007-10-01
I am trying to run a bin file but I keep get the message this:

~/Desktop$ ./WRT54GL_v4.30.11_011_USA_EN_code.bin
bash: ./WRT54GL_v4.30.11_011_USA_EN_code.bin: cannot execute binary file

This didn't happen with GoogleEarth or RealPlayer (no problems).  I also tried
to install dd-wrt using the bin file but I have the same problem.  Could these files
be zipped somehow?

I also tried to convert to iso files using bchunk but that didn't work either.  Any 
ideas?
Thanks,
diane

---

### Post by pelicanghost on 2007-10-04
I get:

chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory

I have it on the desktop, do I move it anywhere else?

---

### Post by jaygo on 2007-10-06
This sounds odd to me. The dd-wrt & the WRT54... bin files are firmware written for a router, and you usually 'upgrade' it into your router using the GUI. Are you trying to do something with it on your PC? If you're just trying to upgrade your router firmware, I'd recommend the dd-wrt firmware as long as your router is supported.

---

### Post by RomeReactor on 2007-10-06
> **pelicanghost said:**
> I get:

chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory

I have it on the desktop, do I move it anywhere else?

Hi. Move it to your home folder and run the commands again; **or** change to the Desktop in the terminal:
```
cd Desktop
```
before running the commands.

---

