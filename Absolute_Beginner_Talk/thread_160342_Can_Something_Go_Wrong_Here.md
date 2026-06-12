---
title: "Can Something Go Wrong Here?"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-04-14
I accidentally used this command when rashly looking around the forums to get rid of all kubuntu packages: WARNING: DO NOT USE THIS COMMAND AS IT WILL REMOVE THE UBUNTU-DESKTOP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Quote:
 	 	 		 			 				Originally Posted by **GoldBuggie**
 				[I]and for uninstalling kubuntu
 	Code:
 	[LEFT]sudo apt-get remove adept akode akregator amarok ark arts dbus gtk2-engines-gtk-qt gwenview ivman k3b kaddressbook kaffeine-gstreamer kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krfb krita kscd ksmserver ksnapshot ksplash ksvg ksysguard ksystemlog kubuntu-default-settings kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin pmount python-opengl python2.3-opengl python2.4-opengl qca-tls ttf-dejavu vorbis-tools[/LEFT]
 
 [/I]
And so I was taken to a black and white screen but luckily I remembered to type in sudo apt-get install ubuntu-desktop.  My question is: after all this happened, could my system be damaged in any way? 

pmj said: " And for some reason Java, Azureus and totem-xine disappeared at the same time."
but for me these programs did not disappear? instead gmail-notify, firestarter, and aegis-virus scanner disappeared.  could some other programs have disappeared???

---

### Post by Mr. Polite on 2006-04-14
Damaged? Doubtful. The only 'damage' I can think of if the removal of libraries that other apps may depend on, but apt-get is pretty good about preventing that.

Doing```
sudo apt-get install ubuntu-desktop
``` fetches meta data for everything Ubuntu 'needs' as far as the default desktop is concerned. You may need to reinstall individual apps that have gone missing though, and doing ```
sudo apt-get update
``` may also be a good idea.

Maybe using Synaptic is a better idea next time you want to remove a desktop package.

---

### Post by user1397 on 2006-04-14
[quote=Mr. Polite]Damaged? Doubtful. The only 'damage' I can think of if the removal of libraries that other apps may depend on, but apt-get is pretty good about preventing that.

Doing```
sudo apt-get install ubuntu-desktop
``` fetches meta data for everything Ubuntu 'needs' as far as the default desktop is concerned. You may need to reinstall individual apps that have gone missing though, and doing ```
sudo apt-get update
``` may also be a good idea.

Maybe using Synaptic is a better idea next time you want to remove a desktop package.[/quote]
Thank you for the reply, it helped me.

---

### Post by Mustard on 2006-04-14
Later on in the thread you were reading (if I am thinking about the same thread), there were some hints for people to use 'Aptitude' to install things rather than Synaptic or apt-get.  This is pretty good advice, as had you installed the KDE desktop using aptitude it would have been one simple command to uninstall KDE and associated programs.  Aptitude has some features that improve on the way Synaptic and Apt-get work.  The interface for aptitude is nowhere near as friendly looking as Synaptic though, as it runs in terminal. :)

Aptitude can be used very similarly to the way that you use apt-get.  To install kubuntu-deskop you would do this...

```
sudo aptitude install kubuntu-desktop
```

then to uninstall KDE (kubuntu) after you have looked it over...

```
sudo aptitude remove kubuntu-desktop
```

Aptitude would remove all the packages you installed previously with kubuntu-desktop with that one command.  So you can see the advantages it has over apt-get/Synaptic.

I've started using aptitude for 99% percent of the things I install via command line now.  The 1% is usually when I forget to use it. :)

---

### Post by user1397 on 2006-04-14
Thanks guys for all the replies.

---

