---
title: "can't get MP3s to play"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by parts-man73 on 2008-01-02
I just made my new laptop a Vista/Gutsy dual boot, Now I'm trying to play MP3 songs. 

I get a pop-up the the correct codec is not installed, I have it try to find the correct codec, and when I try to install "GStreamer extra plugins" I get the following error

> Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I do that and I get this error
> The following packages have unresolvable dependencies. Make sure that all required repositories are added and and enabled in the preferences. 

gstreamer0.10-plugins-ugly:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable

What am I doing wrong?

I first installed "resricted extras" before I attempted to play a MP3 in the first place. Is that interfering with the GStreamer install?

Thanks,
Brian

---

### Post by PPAAUULL on 2008-01-02
I would say that you should try Automatix. I think that it does a great job at installing the MP3 codecs for you with little hassle. As for your problem I would check if those library files are even in the repos. If they are you might want to install them manually/ seperatly and see if you get any problems that way.

---

### Post by esva on 2008-01-02
why don't you try to install it from the add/remove thingie, I think it installs the other necessary things by itself. I tried to play mp3 with xmml and couldn't, but I listen to them now with exaile which said it was like amarok but light in the add remove thing. You can find there the ugly and bad sets too, I saw them there

---

### Post by PPAAUULL on 2008-01-02
What is the differents between the two? I never knew that.....

---

### Post by GuitarRocker2562 on 2008-01-03
use the file browser, and play the mp3 that way, it will try to install the codec, if that doesn't work, let me know

---

### Post by keeper of the wheel on 2008-01-03
XMMS might be the solution you are looking for. I am a huge ogg vorbis person and haven't ripped an Mp3 in a while.... but if I had one I needed to listen to, or a podcast in Mp3 format, XMMS was the savior!
Hope this helps.

---

### Post by rsambuca on 2008-01-03
Your installation isn't set up quite right.  Open your sources (System -> Administration -> Sources List).  Make sure the Universe, Multiverse, and Main repositories are checked (and the Restricted ones, if you prefer).  Then open a terminal (Applications -> Accessories -> Terminal).  Enter the following code in a terminal and tell us what it says:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by parts-man73 on 2008-01-03
I'll try "sudo apt-get install ubuntu-restricted-extras" when I get home from work today and post the results.

thank you

---

### Post by PPAAUULL on 2008-01-03
> **rsambuca said:**
> Your installation isn't set up quite right.  Open your sources (System -> Administration -> Sources List).  Make sure the Universe, Multiverse, and Main repositories are checked (and the Restricted ones, if you prefer).  Then open a terminal (Applications -> Accessories -> Terminal).  Enter the following code in a terminal and tell us what it says:```
sudo apt-get install ubuntu-restricted-extras
```
Ya but doesn't it ask you if you want to enable those if Ubuntu needs to pull a file from one of them? It shouldn't be giving a problem where the file is uninstalible, shouldn't the file just not be found?
Please correct me if I am wrong.

---

### Post by parts-man73 on 2008-01-03
I think I'll try automatix as well. If I had seen that before I tried other methods, I would have done it that way first.

Is there any way to clean out what I've done so far? (the failed GStreamer install)

---

### Post by OldGrey on 2008-01-03
I would be wary of using Automatix, it is not universally loved, especially when you can do the job easily without it. I suggest that you have a look at the following first:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by PPAAUULL on 2008-01-03
It is not universaly loved that doesn't mean it doesn't work. Besides if the great way that is in Ubuntu already doesn't work then it couldn't be worse. Automatix has never broken my system or even messed with it other then installing what I want and what I tell it to do.

---

### Post by OldGrey on 2008-01-03
I've used it in the past as well with good results. However the fact that that its now easy to achieve all I needed it for without using it and the following warning (quote from the link in my previous post) I don't take the risk. 

"Warning Regarding Alternative Installation Methods
Warning: EasyUbuntu and Automatix are third-party utilities for installing the most commonly requested applications in some Debian-based distributions. They are not supported or recommended by Ubuntu. While they work well for many users, they have also been known to corrupt systems and leave them in a state where they cannot be upgraded to a later Ubuntu release."

---

### Post by hyper_ch on 2008-01-03
Automatix is a great way to get your system broken ;)

Although newer releases tend to do that less often it still has many critical points to it.

---

### Post by parts-man73 on 2008-01-03
The "sudo apt-get install ubuntu-restricted-extras" that [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

suggests was the first thing I tried, but I was still unable to play mp3. Should that alone have made it possible to play mp3 and other restricted formats? Maybe I should concentrate on that.

---

### Post by PPAAUULL on 2008-01-03
Ya and you can go read the FAQ on the Automatix website. The only reason they do that is because Ubuntu does not have control over the company so they do not want to get blamed for any problem that MAY arise.

---

### Post by hyper_ch on 2008-01-03
I think that should have been sufficient... well, if you're using Kubuntu you should install:

kubuntu-restricted-extras

instead

---

### Post by hyper_ch on 2008-01-03
> **PPAAUULL said:**
> Ya and you can go read the FAQ on the Automatix website. The only reason they do that is because Ubuntu does not have control over the company so they do not want to get blamed for any problem that MAY arise.

Have a read through this:  [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by PPAAUULL on 2008-01-03
Have you read [http://ubuntuos.wordpress.com/2007/04/11/automatix-myths-that-need-to-be-cleared-up/](http://ubuntuos.wordpress.com/2007/04/11/automatix-myths-that-need-to-be-cleared-up/)

Ya I read that and now I have desided that a plane could fall outa the sky right on top of me and I am not going to go outside anymore!!! COME ON get real.

---

### Post by hyper_ch on 2008-01-03
sure I have ;)

But did you understand what MJG posted?

---

### Post by PPAAUULL on 2008-01-03
I did read it but I mean if I stated all the things wrong with anything and all the things that could go wrong it would look bad too. all I have to say is myth #4 from the article I posted.

---

### Post by hyper_ch on 2008-01-03
audit the automatix code yourself and check what it does ;) if you understand it, you'd agree with MJG

---

### Post by parts-man73 on 2008-01-03
I get 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


when I run "sudo apt-get install ubuntu-restricted-extras"

---

### Post by parts-man73 on 2008-01-03
Finally figured it out. 

Under "System/Administration/Software Sources" In the updates tab....nothing was checked! I was wondering why I had never seen a notice that updates are available, Especially after a new install, I expected quite a few. Somehow this option was not set up properly.

Once I installed the 150 and some odd updates needed, I was able to install GStreamer without problems.

I'm now listening to a MP3!

---

### Post by rsambuca on 2008-01-03
> **parts-man73 said:**
> Finally figured it out. 

Under "System/Administration/Software Sources" In the updates tab....nothing was checked! I was wondering why I had never seen a notice that updates are available, Especially after a new install, I expected quite a few. Somehow this option was not set up properly.

Once I installed the 150 and some odd updates needed, I was able to install GStreamer without problems.

I'm now listening to a MP3!

If you had read my posts, I had indicated that might be a problem way back in post #7 :)

---

