---
title: "How to install debs without internet connection?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by chemicalgr on 2007-05-23
Hello there I'm a newbie user and i have not an internet connection.I'd like to give me some information on installing .deb files on an "Ubuntu i386 system" without being linked on the internet.(i haven't at this time,i'm posting from an internet corner right now).
Actually how can i create a folder where i want to save various debs in there and by using the apt-get command 
to install them or upgrade the existed ones from there.

thanks for your patience.

---

### Post by chamberlain2006 on 2007-05-23
If you want a packages or "deb" from the repositories, go to packages.ubuntu.com and find the package you want.  To install it, double click on the icon in the file manager.  Then just click install.  You may need to download some dependencies also.

---

### Post by chemicalgr on 2007-05-23
You mean,after choosing the preffered  package from ubuntu site ,saving to my usb drive ,going home transfer the data into ny Ubuntu system ,pasting it on my Desktop,the "add remove program" **will find it**?and i choose install package?
What about the apt-get way?Can i create my repository so that the apt-get will "download" and installing (in a sort of way download ok?) files  from my Hard disk directly?If that possible how can i setup or configure this?

---

### Post by jfinkels on 2007-05-23
> **chemicalgr said:**
> You mean,after choosing the preffered  package from ubuntu site ,saving to my usb drive ,going home transfer the data into ny Ubuntu system ,pasting it on my Desktop,the "add remove program" **will find it**?and i choose install package?
What about the apt-get way?Can i create my repository so that the apt-get will "download" and installing (in a sort of way download ok?) files  from my Hard disk directly?If that possible how can i setup or configure this?

To use "apt-get", "aptitude", or "synaptic", you need to have an internet connection so that your computer can communicate with the official repositories (or you can edit your software sources in "System > Administration > Software Sources" to enable only the CD repository from which you installed Ubuntu...I don't know if there's a way to use an arbitrary folder on the local system as a repository). The apt-* system downloads packages from repositories, stores them in /var/cache/apt/archives, and then installs them using the "dpkg" program.

To install a .deb package without the apt-* system, just navigate to where you have the package and either double-click on it to install it using the GDebi program (which is just a graphical interface to the dpkg program) or in the terminal type "sudo dpkg -i *foobar*.deb", where *foobar* is the name of the .deb file.

I think that you can use the apt-* system to uninstall any package installed using dpkg.

---

### Post by chamberlain2006 on 2007-05-23
To install a downloaded .deb, just double click on the file on your desktop to install.  I don't believe that you can make a  repository from a USB drive.

---

### Post by kevinlyfellow on 2007-05-23
Drop your debs in a folder and open up synaptic.  Go to file and "Add downloaded packages"  Also check out the "Generate script" feature (note, I'm talking about the fiesty release, it may be different for earlier versions.

---

### Post by chemicalgr on 2007-05-23
Thanks for your help guys , can't wait to be reconnected with Internet  again,in order to gain full advantage of the **Ubuntu** system.

---

