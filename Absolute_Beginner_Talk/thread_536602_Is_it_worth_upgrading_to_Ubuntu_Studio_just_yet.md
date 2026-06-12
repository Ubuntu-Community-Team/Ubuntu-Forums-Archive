---
title: "Is it worth upgrading to Ubuntu Studio just yet???"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by multifaceted on 2007-08-27
This is my first actual post, I first want to say thanks for everyone's help and opinion... definitely eased the learning process. I have been using Ubuntu about a month now and love it!... Unfortunately for me, I had to learn about **Ubuntu Studio** after I installed Ubuntu.

I am a music professional and a graphics enthusiast. I'm very eager to learn of new music and art applications with Linux. I have been to the web page and it appears that you can just upgrade by using the terminal with the command shown. Seems easy enough but, I was hoping someone can answer a few of my questions before I proceed:

[LIST]
[*]Will I need to reconfigure my settings after upgrading?

[*]Are there potential complications during the upgrade/install process?

[*]Has anyone ever toyed with or does anyone use **Ubuntu Studio**?

[*]Is there any significance to using **Ubuntu Studio** versus Standard Ubuntu for Audio and Graphics Applications?
[/LIST]

Any thoughts or opinion would be greatly appreciated.

---

### Post by dpar on 2007-08-27
I don't use it, but have you done a search at the ubuntu forums startpage? The results of the search seem kind of overwhelming:)

---

### Post by por100pre1 on 2007-08-27
> **multifaceted said:**
> [*]Will I need to reconfigure my settings after upgrading?

Probably not. I didn't need to.

> **multifaceted said:**
> [*]Are there potential complications during the upgrade/install process?

Some people have experienced some complications, nothing is 100% error proof.

> **multifaceted said:**
> [*]Has anyone ever toyed with or does anyone use **Ubuntu Studio**?

I use it.

> **multifaceted said:**
> [*]Is there any significance to using **Ubuntu Studio** versus Standard Ubuntu for Audio and Graphics Applications?

Not much really. The low latency kernel is from the regular Ubuntu repositories as well as most programs. Only the eye candy, a few programs, and some alsa tools are the real difference in Ubuntu Studio. It is actually a collection of software and tools in Ubuntu.

Want to install it?

If using Feisty do this:

Add the Ubuntu Studio repository:
```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then install Ubuntu Studio:

```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

**(If using Gutsy just do the last step, Ubuntu Studio is in the Gutsy repositories.)**

Hope this helps.
:guitar:

---

### Post by multifaceted on 2007-08-28
> **dpar said:**
> I don't use it, but have you done a search at the ubuntu forums startpage? The results of the search seem kind of overwhelming:)

I did search the forums start page but, wasn't quite getting the answers I was looking for. :-|

However, from what I can tell from what others have posted is that there is not quite much difference

---

### Post by multifaceted on 2007-08-28
> **por100pre1 said:**
> Probably not. I didn't need to.



Some people have experienced some complications, nothing is 100% error proof.



I use it.



Not much really. The low latency kernel is from the regular Ubuntu repositories as well as most programs. Only the eye candy, a few programs, and some alsa tools are the real difference in Ubuntu Studio. It is actually a collection of software and tools in Ubuntu.

Want to install it?

If using Feisty do this:

Add the Ubuntu Studio repository:
```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then install Ubuntu Studio:

```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

**(If using Gutsy just do the last step, Ubuntu Studio is in the Gutsy repositories.)**

Hope this helps.
:guitar:

Yes, very big help, thanks!  Ha ha, agreed, I always figure nothing will ever go 100% right. I was just wondering if there was any kind of common fluke that could be avoided.

Thanks for the tips and the commands for the terminal! :)

I am still a *little* weary of upgrading just yet, want to be sure it's just not a waste of time. I already use the Ubuntu Studio theme and have multimedia running swiftly.

So you use it, what's your overall opinion on it? 

Do you ever use it for audio capture? Or digital recording, sampling or sequencing? I am interested to see if I am able to throw down some guitar tracks and audio editing.  If so, what kind of hardware or interfaces would that require? I've used Cubase and Reason with Windows for a while now.... looking for a Linux alternative :cool:

---

