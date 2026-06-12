---
title: "Newbie question: how do you install themes"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by moseefus on 2007-01-25
**[FONT="Arial Black"][SIZE="3"]Dear Ubuntu community, I just partitioned ubuntu and windows to my laptop and it is my 2nd time using ubuntu. I have ubuntu 6.10 and I was wondering what type of theme can I install to it and what is the step by step process for installing the theme.:D [/SIZE][/FONT]**

---

### Post by rabid emu on 2007-01-25
Assuming you're using Gnome, just look around here [http://www.gnome-look.org/](http://www.gnome-look.org/) for a theme you like, download it, and then go to system -> preferences -> themes -> install theme and find the theme you downloaded from your directory.

---

### Post by ardchoille42 on 2007-01-25
The above is good for single themes. However, if you install a multi-theme tarball and find the theme doesn't work, or you try to install a theme which wasn't packaged correctly, then the theme manager won't be of help.. the theme manager has trouble installing multi-theme tarballs correctly. If this should happen, you can always unpack the tarball into ~/.themes (for user only themes) or /usr/share/themes (for system wide theme use). All the theme manager does when it installs a theme is unpack it and copy the theme to ~/.themes anyway.

some good theme sites:

[http://www/gnome-look.org](http://www/gnome-look.org)
[http://art.gnome.org](http://art.gnome.org)

---

### Post by jimbo111 on 2007-02-12
I'm having a problem just installing any theme. I'm using the Silicon theme right now but find the default ones boring. I've wanted to install new themes, so I first went to Synaptic Package Manager, installed a bunch of gtk2-engine themes....I can find them in the /usr/share/Themes folder, but when I try to install it using the Themes Install button, I select a theme which is  in the /usr/share/Themes folder, it opens, I then see either a gtk-2.0 folder or a metacity folder. For the gtk-2.0 folder, I'll see a gtkrc file, when I try to open it, I get "The file format is invalid".....and any file in the metacity folder gives me the same result.....So...how do you install themes in Ubuntu for gnome??? :confused:

---

### Post by jtapper on 2007-02-12
As ardchoille42 wrote earlier one easy way for installing a theme is to unpack the tar.gz -file containing the theme files to /usr/share/themes directory.
From there every user can pick a theme of their choice to be used.

Once the theme is unpacked you don't have to install anything. Just do System-Preferences-Themes and find your theme.

---

### Post by Homebrew on 2007-02-16
I get an error "You don't have the right permissions to extract archives in the folder "/usr/share/themes"" when attempting to extract the tar file into /usr/share/themes directory.

I'm logged into the only account in Ubuntu so I'm assuming it is the root user.  I am not prompted for a password.

What step am I overlooking?

Ubuntu 6.10 fresh install.

---

### Post by Maestro23 on 2007-02-16
> **Homebrew said:**
> I get an error "You don't have the right permissions to extract archives in the folder "/usr/share/themes"" when attempting to extract the tar file into /usr/share/themes directory.

I'm logged into the only account in Ubuntu so I'm assuming it is the root user.  I am not prompted for a password.

What step am I overlooking?

Ubuntu 6.10 fresh install.

You are writing to a directory that is owned by [COLOR="Red"]"root"[/COLOR], therefore you need [COLOR="Red"]"sudo"[/COLOR] in front of your terminal commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Homebrew on 2007-02-16
Thank you for your reply.  I realized the issue was related to permissions.  I was asking how to install the package into the folder by the GUI.  I will use the opportunity to research the command line and find a solution.

Thank you again!

---

### Post by Homebrew on 2007-02-16
I have spent a bout 2 hours rin the last 3 days researching google, gnome-look.org, gnomethemes.org on how to install a new theme but eery attempt has failed. 

I download a theme to my desktop.  I extract it to my desktop.  I use Terminal to move the new folder to /usr/share/themes

I go to System>Prefs>Themes and my theme does not show up.

I can go System>Prefs>themes>Install theme  then locate the folder /usr/share/themes but anything I select gets an Invalid File format error.

What am i overlooking?

Thanks in advance.

---

### Post by jtapper on 2007-02-17
@ homebrew:

Then try dragging tar.gz that contains your theme into themes-application.
This way you can make changes to current theme and you don't have to have full, for example, GTK2 theme or metacity theme. I found this the easiest way for changing icons for instance.

---

### Post by Homebrew on 2007-02-18
Thank you that worked.  You are the best!

---

### Post by azurehi on 2007-02-19
I have tried all the suggestions in this thread but cannot install this theme (only one I've downloaded):/home/neil/Desktop/blueswirl.tar.bz2
/home/neil/Desktop/BlueSwirl
I don't understand what to put in terminal:  sudo install blueswirl doesn't work; opening /usr/share/themes and dragging the .tar.bz.2 or the blueswirl from the desktop results in something like "you don't have permission...".  Archieve manager doesn't help - is unpacking a .tar the same as extracting.  Very:confused:  confused

---

### Post by jtapper on 2007-02-20
Azurehi:

Blueswirl is a GDM theme. You need to install it as follows:
Sytem-Administration-Login window
from there click Add -button and find your blueswirl.tar.bz2 file. It should now appear on the list. 

Hopefully you understand that it is just gdm-theme and therefore it will only change appearance of login screen.

---

### Post by il-luzhin on 2007-03-06
first time linux user.   Same prob as home brew

Where is themes-application folder?

---

### Post by Pulp-o-rama on 2008-03-22
I'm also trying to install the blueswirl theme, day 2 of noodling around in Ubuntu.  When I try to add the GDM theme from the Login Window Preferences, it doesn't recognize the .tar.bz2 file as a theme.  Should I repackage the file as a .tar.gz?  how would I do that?

---

### Post by Pulp-o-rama on 2008-03-22
Aha, I just had to open my mouth to turn my brain on.  I extracted the .tar.bz2 to a themes folder, then made a new blueswirl.tar.gz archive.  It was recognized and it works!

---

