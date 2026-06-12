---
title: "How to get Linux drivers off MOBO CD?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by berlin58 on 2007-07-21
Is there an easy way for a newbie to get the video and audio drivers from my ASUS MOBO CD installed?
NVidia GeForce 6150 Chipset on MOBO. VGA and DVI out needed.
Thanks

---

### Post by pyros on 2007-07-21
> **berlin58 said:**
> Is there an easy way for a newbie to get the video and audio drivers from my ASUS MOBO CD installed?
NVidia GeForce 6150 Chipset on MOBO. VGA and DVI out needed.
Thanks
a
No, not to the best of my knowledge, because they are intended for windows, not for linux. try going to System>Administration>Restricted Drivers Manager to install nvidia's driver.

---

### Post by berlin58 on 2007-07-21
The MOBO CD has the LINUX drivers in addition to the WIN drivers

Restricted Drivers Manager reports:       getit has not been able to detect the caracter coding
        choice:            Current Locale UTF-8
                                Western ISSO 8859-15
Does this mean that these LiNUX drivers may not be compatible with UBUNTU installations?
Thanks

---

### Post by pyros on 2007-07-21
> **berlin58 said:**
> The MOBO CD has the LINUX drivers in addition to the WIN drivers

Restricted Drivers Manager reports:       getit has not been able to detect the caracter coding
        choice:            Current Locale UTF-8
                                Western ISSO 8859-15
Does this mean that these LiNUX drivers may not be compatible with UBUNTU installations?
Thanks

you have me at a total loss there. As far as I know the restricted drivers manager should install the nvidia driver that is prepackaged for ubuntu. You might ought to repost that error in the multimedia and video section of the forums.

---

### Post by berlin58 on 2007-07-22
> **pyros said:**
> you have me at a total loss there. As far as I know the restricted drivers manager should install the nvidia driver that is prepackaged for ubuntu. You might ought to repost that error in the multimedia and video section of the forums.

You are so right pyros, it just took a while for me to figure out how to download the nVidia restricted driver and change from "not in use" button.

Unfortunately the nVidia prepackaged for ubuntu driver still gives me low quality video (1024--- 50Hz) and I would like to learn how to install the ASUS  Linux drivers from my MOBO CD. May be you can give me some hints?
Besides the nVidia driver there is a Nforce Linux driver and an Audio(Soundmax ADI 1986A alsa-project) Linux driver on my CD.
Thanks

---

### Post by pyros on 2007-07-22
> **berlin58 said:**
> You are so right pyros, it just took a while for me to figure out how to download the nVidia restricted driver and change from "not in use" button.

Unfortunately the nVidia prepackaged for ubuntu driver still gives me low quality video (1024--- 50Hz) and I would like to learn how to install the ASUS  Linux drivers from my MOBO CD. May be you can give me some hints?
Besides the nVidia driver there is a Nforce Linux driver and an Audio(Soundmax ADI 1986A alsa-project) Linux driver on my CD.
Thanks

What format are they in? tgz, tar.gz, rpm, deb, bin?

---

### Post by berlin58 on 2007-07-23
The drivers have a .run extension.
Here is a readme file:

1.0-8174 web candidate for x86/x86_64 (Driver)
 
Description:
1.0-8174 web candidate for x86/x86_64

Changlog -
* Added support for SLI FrameRendering. Please see the README for details.
* Added support for new GPUs such as the GeForce 6100 and GeForce 6150.
* Added a new utility 'nvidia-xconfig', which is a commandline tool for updating X configuration files.
* Added manpages for 'nvidia-xconfig', 'nvidia-settings', and 'nvidia-installer'.
* Improved workstation OpenGL performance on Solaris.
* Made UseEdidFreqs "on" by default; the NVIDIA X driver will use the valid HorizSync and VertRefresh frequency ranges from the EDID whenever possible.
* Added support for Stereo Digital Flat Panels such as the SeeReal and Sharp3D DFPs.
* Added HTML version of the README.
* Added support for static Rotation; see the "Rotate" X config option in the README.
* Improved stability on 64-bit Linux 2.6 kernels.
* Fixed driver installation when SELinux is enabled

 
Version: 1.0-8174
 
 
Driver Type: Official Build
 
Driver Release: Linux
 
Operating System: Linux
----------------------------------------------------------------------------------------------
I also have a new GeForce 8500 GT card which I like to install as soon as I have my MOBO video working properly. I don't have the Linux driver for this board yet.

Thank you very much for taking the time to help me out.

---

### Post by asmoore82 on 2007-07-23
I can almost assure you that the drivers ubuntu loads are waaay more up to date than the ones on any Mobo CD

---

### Post by pyros on 2007-07-23
> **asmoore82 said:**
> I can almost assure you that the drivers ubuntu loads are waaay more up to date than the ones on any Mobo CD

While I absolutly agree with asmoore here, If you are dead set on trying them, copy the files to your harddrive, someplace easy to get to like the Desktop. Right click on the .run file, and go to properties. Go to the permissions tab, and check "Allow executing file as program" then click on the close button. now open a terminal, and go to the folder with the .run file. If you did place it on the desktop, the command "cd ~/Desktop" will get you there. Then type the name of the file, and press enter. If you have any problems with that, be sure to copy anything that the .run file says and include that text with your post.

---

### Post by berlin58 on 2007-07-24
> **asmoore82 said:**
> I can almost assure you that the drivers ubuntu loads are waaay more up to date than the ones on any Mobo CD
Being a complete newbie I will have to believe you, asmoore, but I would think that you could tell me then why the nVidia prepackaged for ubuntu driver still gives me, as maximum, a low quality video (1024--- 50Hz), while my hardware supports double that resolution @ 75Hz??? 

 Please tell me what I can do to my software installation,  to get the choice of setting my monitor for a better display. 
Thank you pyrus for your advice and instructions which I will use only if there is no other means to get my video going
Thanks

---

