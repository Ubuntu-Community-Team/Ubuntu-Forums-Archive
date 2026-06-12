---
title: "CD Recording Software"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2005-11-27
People,

I looked for it in the Synaptic utility and I could not find any package that would enable me to record CDs.

What is the recommended CD burning software for Linux?

---

### Post by sarah_b on 2005-11-27
I personally like K3b

---

### Post by Joey French on 2005-11-27
K3b. It is simply the best I have found for Linux. There is NeroLinux, but it's non-free. There is also gnomebaker and others, but I would suggest K3b first.

---

### Post by ssam on 2005-11-27
if you want to make a data cd then just put a blank cd in the drive and it will appear as a folder you can drag files to. then when you are done click burn.

there is serpentine which should already be installed, and has an icon in the sound and video menu.

if you want to burn an iso file, then write click on it can choose "burn to disk"

if you want to do more advanced stuff then you can install graveman, gnomebaker or k3b.

---

### Post by paulozzzz on 2005-11-27
[QUOTE=sarah_b]I personally like K3b[/QUOTE]

Will it work under Gnome?

---

### Post by paulozzzz on 2005-11-27
"if you want to make a data cd then just put a blank cd in the drive and it will appear as a folder you can drag files to. then when you are done click burn."

This is interesting, but I will need to keep the CD open for new sections.

"there is serpentine which should already be installed, and has an icon in the sound and video menu."

This is not available in the default installation.  Perhaps in Synaptic?

"if you want to burn an iso file, then write click on it can choose 'burn to disk'"

Interesting.

"if you want to do more advanced stuff then you can install graveman, gnomebaker or k3b."

I will try these, thanks.

---

### Post by jackmacokc on 2005-11-27
[QUOTE=paulozzzz]Will it work under Gnome?[/QUOTE]

sudo apt-get install k3b

yes it will work!

---

### Post by Joey French on 2005-11-27
I have never had a problem using k3b under Gnome, or KDE, or ever for that matter.

---

### Post by paulozzzz on 2005-11-27
Where can I download Gnomebaker from?  I tried Google and all what I could find are links to forum threads but no download links.  I tried download.com and the search engine yielded no results.:confused:

---

### Post by ssam on 2005-11-27
as people have said k3b will work in gnome. but as it uses the qt and kdelibs it will look very different from gnome apps, and require downloading quite a few dependancies.

---

### Post by paulozzzz on 2005-11-27
[QUOTE=jackmacokc]sudo apt-get install k3b

yes it will work![/QUOTE]

The apt-get command did not work.

Translated bash output follows:

Reading package list... Ready
Building dependency tree... Ready
E: Impossible to find package k3b

:(

Do I need to insert the installation CD?

---

### Post by Joey French on 2005-11-27
Synaptic should turn up Gnomebaker. You should get into the habit of checking Synaptic first, it is a godsend when it comes to adding programs.

---

### Post by paulozzzz on 2005-11-27
[QUOTE=Joey French]Synaptic should turn up Gnomebaker. You should get into the habit of checking Synaptic first, it is a godsend when it comes to adding programs.[/QUOTE]

What is the name of the package?

I tried Synaptic's search tool (Name and Description) and again nothing was found.

---

### Post by Joey French on 2005-11-27
Both Gnomebaker, and K3b show up in my Synaptic. Have you expanded your repositories? If not, I will help oyu get that taken care of.

---

### Post by paulozzzz on 2005-11-27
[QUOTE=Joey French]Both Gnomebaker, and K3b show up in my Synaptic. Have you expanded your repositories? If not, I will help oyu get that taken care of.[/QUOTE]

How do I expand my repositories?  Thanks for the help.

---

### Post by Joey French on 2005-11-27
Okay, in a terminal type in this:
```
sudo cp /etc/apt/sources.list 
/etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

```
This will backup your old repo list, and then you will edit it with gedit.
Paste this OVER your repository list (I assume you are running Breezy- if not stop right there, and tell me otherwise!:
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```
Then, you will save and exit.
Go into Synaptic, and hit reload. You will most certainly see it then.

Any questions at all, or if you are not sure of what you are doing, reply here soon.

---

### Post by gpw797 on 2005-11-27
Give the search function a try, tons of info here on repositories. Think Gnomebaker is in universe. Also option to install it with Automatix

---

### Post by paulozzzz on 2005-11-27
Thanks, people.  The solutions worked.:D

---

### Post by Joey French on 2005-11-27
Good to hear. Now that your repositories are expanded, you may want to go to Synaptic, hit "Reload", then "Mark all Upgrades", then "Apply". It will probably have a bunch of updates to install for you. 

Reloading Synaptic is a good idea, as it refreshes the package list available for your system. It keeps you up to date, and gives the largest pool of resources with which to find what you're looking for.

---

### Post by paulozzzz on 2005-11-27
[QUOTE=Joey French]Good to hear. Now that your repositories are expanded, you may want to go to Synaptic, hit "Reload", then "Mark all Upgrades", then "Apply". It will probably have a bunch of updates to install for you. 

Reloading Synaptic is a good idea, as it refreshes the package list available for your system. It keeps you up to date, and gives the largest pool of resources with which to find what you're looking for.[/QUOTE]

Thannks.  But I still want to know exactly the purposes of each package.  Furthermore there is currently only 5GB available for Ubuntu in my system.  As Linux becomes more and more important for my work I will add more space for its partition.\\:D/

---

### Post by paulozzzz on 2005-11-27
Unfortunatelly Gnomebaker is not exactly what I wanted.  It lacks multisession capability.:???: 

Is there a CD burner that supports multisession?

---

### Post by GreenHawkIA on 2005-11-27
I'm pretty sure K3B does.  And I thought Gnomebaker did too, but I'm not sure.  To get K3B (the best CD burning software on any platform - including MS), just open a terminal and type sudo apt-get install k3b.

---

### Post by paulozzzz on 2005-11-28
[QUOTE=GreenHawkIA]I'm pretty sure K3B does.  And I thought Gnomebaker did too, but I'm not sure.  To get K3B (the best CD burning software on any platform - including MS), just open a terminal and type sudo apt-get install k3b.[/QUOTE]

Thank you.  I will try this as soon as I get home.  The package shows in Synaptic, but I need a working internet connection to get it as my target system's winmodem is still not working.:)

---

### Post by paulozzzz on 2005-11-28
[QUOTE=GreenHawkIA]I'm pretty sure K3B does.  And I thought Gnomebaker did too, but I'm not sure.  To get K3B (the best CD burning software on any platform - including MS), just open a terminal and type sudo apt-get install k3b.[/QUOTE]

Thanks for the tip.  It works, even under Gnome.

---

### Post by SumoJim on 2005-11-29
I've been trying to get my DVD burner to work as well.

"sudo apt-get install k3b

yes it will work!"

Didn't work for me at all. Didn't do anything that I could tell except write a few interesting things in my command prompt though I didn't know what any of it ment.

I say stick with GNOME programs if you can find them.

---

### Post by kperkins on 2005-11-30
[QUOTE=paulozzzz]Where can I download Gnomebaker from?  I tried Google and all what I could find are links to forum threads but no download links.  I tried download.com and the search engine yielded no results.:confused:[/QUOTE]

Never mind--I should read the whole thread, my eyes were playihg tricks on me.

---

### Post by Estariel on 2005-11-30
[QUOTE=SumoJim]I've been trying to get my DVD burner to work as well.

"sudo apt-get install k3b

yes it will work!"

Didn't work for me at all. Didn't do anything that I could tell except write a few interesting things in my command prompt though I didn't know what any of it ment.

I say stick with GNOME programs if you can find them.[/QUOTE]

Well, you'll have to start k3b after installing it...?
just type "k3b" on the command prompt.

And there are at least two KDE programs that just don't have an equal in the GNOME world... K3B and amaroK

---

### Post by SumoJim on 2005-11-30
Ok, I typed k3b in the command line and it worked... sort of. 

I reported about 50 errors and then the application pops-up anyway. Along with an error message saying:

Unable to find cdrdao executable
K3b uses cdrdao to actually write CDs.
Solution: Install the cdrdao package.


So, I decided to try to figure out synaptic.... I did not see cdrdao
I looked for gnomebaker while i was at it with no luck. After reading over the thread again I realized I may need to "expand my repositories"

I see a demonstration int this thread for expanding repositories for "Breezy Badger" but I have "Hoary Hedgehog"

Once I get my CD Burner working I plan to make a "Breezy Badger" install CD.

So, my question is... How do I expand my repositories for "Hoary Hedgehog"?

Also, how does this expansion work? Will I need to change the file every time I want to expand the repositories?

---

### Post by detyabozhye on 2005-12-01
Maybe it's not important anymore, but GnomeBaker messed up on burning an audio CD, it was slow and only burnt three tracks, DON'T burn audio CDs with GnomeBaker! Tried K3B after that, and it worked perfectly.

---

### Post by solarcontrol on 2005-12-01
I've always liked xcdroast, but k3b is the easiest.
Never had a bit of trouble with it either.

---

