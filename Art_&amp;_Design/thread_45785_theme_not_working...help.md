---
title: "theme not working...help"
date: 2005-07-01
forum: Art &amp; Design
---

### Post by jamesford on 2005-07-01
Hello!

i'm quite new to this. I fell in love with this theme [http://gnome-look.org/content/show.php?content=23563&PHPSESSID=92dcb454dd5f5758799237aae1a5e921](http://gnome-look.org/content/show.php?content=23563&PHPSESSID=92dcb454dd5f5758799237aae1a5e921)

It worked for me before, but now it just doesent work anymore, the system reverts to the basic gray style...

my ubuntu is up2 date if that matters

---

### Post by monchichi on 2005-07-01
yup, thats a great theme.. make sure you have the clearlooks engine installed, i.e.: ```
sudo apt-get install gtk2-engines-clearlooks
``` or search for clearlooks in synaptic.

If that doesnt work, navigate to your ~/.themes folder, delete the old gperfection folder, and downlaod and extract a new one in its place.

good luck!

---

### Post by jamesford on 2005-07-01
i appreaciate the help but it simply didnt work :( did just as u said but it still reverts to grey. all other clearlooks themes work, just not this one :(

---

### Post by Neo40 on 2005-07-16
[QUOTE=jamesford]i appreaciate the help but it simply didnt work :( did just as u said but it still reverts to grey. all other clearlooks themes work, just not this one :([/QUOTE]

I have the same problem. Someone can help?
Thanks

---

### Post by Paool on 2005-07-16
You need to have Clearlooks engine in 0.6 version :) It's in backports repositories.

---

### Post by Neo40 on 2005-07-16
[QUOTE=Paool]You need to have Clearlooks engine in 0.6 version :) It's in backports repositories.[/QUOTE]
Hi,

I have 0.5 version installed. I don't see 0.6 version with Synaptic. I have backports repositories.

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

???

EDIT: Nermind. I compiled it myself from [http://www.gnome-look.org/content/show.php?content=19527](http://www.gnome-look.org/content/show.php?content=19527)

---

### Post by Paool on 2005-07-16
sorry, it's in backports-staging :) 

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

---

### Post by Jason-X on 2005-07-22
I'm having the same trouble with this theme. I just can't get it to work. 

I'm using Ubuntu Hoary on PPC. Mine comes out blue :???: 

[IMG]http://img301.imageshack.us/img301/7696/shot6kz.png[/IMG]

---

### Post by Jason-X on 2005-07-22
[QUOTE=Paool]sorry, it's in backports-staging :) 

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted[/QUOTE]

Thanks!! This did the trick :)

---

### Post by pailhead on 2005-07-23
[QUOTE=Paool]sorry, it's in backports-staging :) 

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted[/QUOTE]

I added that to my sources.list and still can't find 0.6 of clearlooks. What command did you use to get it? apt-get install "what title?"

I checked Synaptic and only shows .5

---

### Post by Jason-X on 2005-07-24
I added these lines to my sources.list:

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

I updated and used Synaptic to search for "Clearlooks". It found 0.6.

---

### Post by pailhead on 2005-07-24
[QUOTE=Jason-X]I added these lines to my sources.list:

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## Backports Staging
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

I updated and used Synaptic to search for "Clearlooks". It found 0.6.[/QUOTE]

That's strange... I've attached my sources.list anything I"m missing?

---

### Post by Jason-X on 2005-07-24
Your sources are the same as mine.

If you search for "clearlooks" on Synaptic you should get this result:

**gtk2-engines-clearlooks**

If you right-click >properties you will see tab labelled "versions". I have both versions listed in this:

[B]0.6.2-1~5.04ubp1 (now)
0.5-0ubuntu1 (hoary)[/B]

I don't now if you have both versions listed. If you do you may be able to choose "Package>Force Version.." from the menu.

Hope this helps :)

---

