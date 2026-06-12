---
title: "problems with installing downloded software"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by neo_009 on 2007-09-26
hi i am new to ubuntu.

i am trying to install a python tool for molecular docking called autodock, since autodock is not compitalble with vista, i have to install ubuntu and now i am trying to install that software which i downloded in form of *.tar.gz file but i dont know it seems that it is not working.  I have tried Add/remove application, i have tried synaptic package manager but all in vain.

can anyone help me with that.

the software which i am trying to install can be found at [http://mgltools.scripps.edu/downloads](http://mgltools.scripps.edu/downloads).

Please if anyone know how to deal with this problem, kindly send me the method of installing this software.  

Please if possible give me method in detail since i am terrible with working on command line.

cheers!!!

---

### Post by overdrank on 2007-09-26
HI the first file to download is a bin file. Have you tried that one and it does start if you download the tar to use the read me file.
Edit and this may help
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by dwhitney67 on 2007-09-26
> **neo_009 said:**
> hi i am new to ubuntu.

i am trying to install a python tool for molecular docking called autodock, since autodock is not compitalble with vista, i have to install ubuntu and now i am trying to install that software which i downloded in form of *.tar.gz file but i dont know it seems that it is not working.  I have tried Add/remove application, i have tried synaptic package manager but all in vain.

can anyone help me with that.

the software which i am trying to install can be found at [http://mgltools.scripps.edu/downloads](http://mgltools.scripps.edu/downloads).

Please if anyone know how to deal with this problem, kindly send me the method of installing this software.  

Please if possible give me method in detail since i am terrible with working on command line.

cheers!!!
Choose the binary download that is appropriate for your system (either the 32-bit or 64-bit).  The choices are adjacent to the Linux Penguin.

After you have chosen which distro to download, the instructions page will appear.

Once the download is complete, navigate to the folder where the file was downloaded.  Right-click on the file and select **Properties**.  Then select the **Permissions** tab.  Then check the box that enables **Execute** permissions on the file.  Then close the properties dialog box.

Next, double-click on the icon of the downloaded package.  From there onwards the "wizard" will guide you through the installation of the software application.

---

### Post by mesilliac on 2007-09-26
It sounds like you downloaded the source code. That site you linked has a binary installer, that would be much easier to use. Just download that and follow the installation instructions, which are also linked on that site. You most likely want the "Unix/Linux - x86" file.

---

### Post by equinox_child on 2007-09-26
You seem to have downloaded the source code. Assuming, from you're introduction, that you're new to linux, compiling from source may be a bit difficult (albeit not impossible). The site you provided has a linux binary, which is similar to how you would normally install programs in windows (that is, it runs a setup and installs itself).

Follow dhitney's explanation for how to run the binary.

---

