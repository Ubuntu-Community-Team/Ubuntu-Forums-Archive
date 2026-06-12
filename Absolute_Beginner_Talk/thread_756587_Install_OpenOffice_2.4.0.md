---
title: "Install OpenOffice 2.4.0?"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by kuproverto on 2008-04-16
I'm completely new to Linux and I've just installed Ubuntu 7.10. I'm trying to figure out how to install OpenOffice 2.4.0. 

So far I've downloaded the file from the OpenOffice site and I now have the OOH680_m12_native_packed-1_en-US.9286 folder siting on my Desktop. What do I do next? I've double clicked the setup file inside this folder to no avail. Please help!

---

### Post by calc on 2008-04-16
The easiest way would be to install Ubuntu 8.04 when it is released on Apr 24, a little over a week from now.

---

### Post by deanjm1963 on 2008-04-16
First you need to download the correct version of openoffice for ubuntu.

When you go to their website and select to download it, instead of clicking on "Download now!" click on the link underneath that says, "Get more platforms and languages", once on that page, you need to select "Linux Deb" for your appropriate language.

Once downloaded extract the archive. You will have a folder with a couple of other folders inside.

The easiest way to install this is as follows:

1. Make a folder on your desktop called oo24

2. Copy every .deb file (including the debian menus .deb) into that folder called oo24

3. First open synaptic and make sure you have a filed called "libgmp3c2" installed, openoffice requires it. (Make sure you close synaptic afterwards)

4. Open a terminal and type: cd /home/(your username)/Desktop/oo24

5. Type the following: sudo dpkg -i *.deb

You will be prompted for your password.

Once installed, log out to refresh the menus, once you log back in, OpenOffice 2.4 should be up and running.

Hope this helps.

---

### Post by kuproverto on 2008-04-16
calc - I'll install v8.04 when it's released but, as I've never used Linux before, I wanted to get my feet wet with this version.

deanjm1963 - Thanks, I've followed your instructions but now I have a broken package. In the Synaptic Package Manager it's listed as 'openoffice.org-onlineupdate' version 2.4.0-12.

That onlineupdate file is also the last one listed in the terminal window before the ~/Desktop/oo24$ line.

What went wrong?

---

### Post by Toadinator on 2008-04-16
> **kuproverto said:**
> I'm completely new to Linux and I've just installed Ubuntu 7.10. I'm trying to figure out how to install OpenOffice 2.4.0. 

So far I've downloaded the file from the OpenOffice site and I now have the OOH680_m12_native_packed-1_en-US.9286 folder siting on my Desktop. What do I do next? I've double clicked the setup file inside this folder to no avail. Please help!

You may want to just wait until the 24th and upgrade to 8.04 Hardy. What I don't understand is why when people ask for support they're usually told to type something in on the command line. What you should do is check if 2.3 is not already installed by clicking on the Applications menu and looking under office. If it is then you don't need to worry. It'll get updated along with your Ubuntu version on the 24th.

---

### Post by Oldsoldier2003 on 2008-04-16
> **Toadinator said:**
> You may want to just wait until the 24th and upgrade to 8.04 Hardy. **What I don't understand is why when people ask for support they're usually told to type something in on the command lin**e. What you should do is check if 2.3 is not already installed by clicking on the Applications menu and looking under office. If it is then you don't need to worry. It'll get updated along with your Ubuntu version on the 24th.

Because when you use the command line it's faster and more efficient. Plus the poster can copy and paste, so we know exactly what is going on and what should be happening, rather than wading through a bunch of menus to skin the cat one of 5 ways...

---

### Post by kuproverto on 2008-04-16
I'll definitely install Hardy when it's released.

I don't mind using the command line if it's the quickest and most efficient way to use Linux but I was wondering, is there an equivalent way of installing a downloaded software application to double clicking a setup.exe like in Windows?

---

### Post by Oldsoldier2003 on 2008-04-16
> **kuproverto said:**
> I'll definitely install Hardy when it's released.

I don't mind using the command line if it's the quickest and most efficient way to use Linux but I was wondering, is there an equivalent way of installing a downloaded software application to double clicking a setup.exe like in Windows?

It depends on what it is. For instance if you downloaded a .deb file you could double click or right click and open with GDebi installer. However many things you download either need to be compiled or an install script is run. You can run a script by right click, run in terminal, but in order to compile source you have to use the terminal.

---

### Post by stchman on 2008-04-16
> **kuproverto said:**
> I'm completely new to Linux and I've just installed Ubuntu 7.10. I'm trying to figure out how to install OpenOffice 2.4.0. 

So far I've downloaded the file from the OpenOffice site and I now have the OOH680_m12_native_packed-1_en-US.9286 folder siting on my Desktop. What do I do next? I've double clicked the setup file inside this folder to no avail. Please help!

OO's website has a DEB version that works well.  I run it on Feisty with no problem.  Download the DEB version and install all the DEBs.  Don't forget the debian menus deb in the desktop-integration folder.

---

### Post by calc on 2008-04-16
> **deanjm1963 said:**
> First you need to download the correct version of openoffice for ubuntu.

When you go to their website and select to download it, instead of clicking on "Download now!" click on the link underneath that says, "Get more platforms and languages", once on that page, you need to select "Linux Deb" for your appropriate language.

Once downloaded extract the archive. You will have a folder with a couple of other folders inside.

The easiest way to install this is as follows:

1. Make a folder on your desktop called oo24

2. Copy every .deb file (including the debian menus .deb) into that folder called oo24

3. First open synaptic and make sure you have a filed called "libgmp3c2" installed, openoffice requires it. (Make sure you close synaptic afterwards)

4. Open a terminal and type: cd /home/(your username)/Desktop/oo24

5. Type the following: sudo dpkg -i *.deb

You will be prompted for your password.

Once installed, log out to refresh the menus, once you log back in, OpenOffice 2.4 should be up and running.

Hope this helps.

Don't forget that if you install OpenOffice.org this way you will have to remove it manually before upgrading to Ubuntu 8.04 (hardy).

---

### Post by kuproverto on 2008-04-16
Thanks for the replies. It looks like there's going to be a bit of a learning curve with Ubuntu. I think I'll buy a book and spend a few days surfing the many Linux sites.

---

### Post by Bladerunr on 2008-05-10
I've just installed 8.04 Hardy and it does come with OO2.4 but only a few of the full office suite. I need the draw app too. I am equally new to Ubuntu and the linux world, trying to install OO2.4, struggling despite 23 years in IT, it should be easier :-(

I've browsed the Ubuntu online help docs, just can't seem to find any reference to 'installing applications' or 'installing OO2.4' that doesn't use Linux jargon and cryptic commands.

The install instructions should be '*download, click install and follow the on screen prompts*' surely?

---

### Post by erginemr on 2008-05-10
@Bladerunr

Don't worry, it also surprised me to see only part of OpenOffice installed. I guess this decision was taken to fit the contents of the installed into a single CD.

Anyway, it is very easy to complete the OOo suite. You need to browse to Menu -> System -> Admin -> Synaptic find the packages "OpenOffice Base" (Database component) and "OpenOffice Draw".  (The names may not be exact, but you get the idea.) You can then install them to complete the suite.

"OpenOffice Base" will also try to load a Java environment, by default, the open-source gcj suite. You may also take the lead and install Sun Java (sun-java6-jre) instead, before the installation of OOo Base.

If you need a vector drawing program, you can also try "inkscape" and "xaralx" from Synaptic, both of which are very capable vector graphics software.

---

