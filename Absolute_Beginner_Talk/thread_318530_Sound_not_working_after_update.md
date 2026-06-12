---
title: "Sound not working after update"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Pobega on 2006-12-14
I updated my computer this morning after it prompted me that there was an update available, and after restarting I noticed that my sound wasn't working.

When I try to use XMMS I get this error:
[i]Please check that:
Your soundcard is configured properly
You have the correct output plugin sound
No other program is blocking the sound[/i]

Any help to get the sound working would be appreciated, because now I can't listen to Howard Stern!

My sound card is "Sound: Intel High Definition Audio " according to the site I bought the laptop from (System76)

**Edit:** Unedited

**Edit2:** In my rush to search for help I posted this in the wrong section, so if a mod can please move this thread it would be much appreciated.

**Edit3:** I followed all of the steps in [this thread](http://ubuntuforums.org/showthread.php?t=205449) but when I run aplay -l I still get > pobega@ubuntu:~$ aplay -l
aplay: device_list:222: no soundcards found...

**Edit4:** For those who are interested or may find this helpful, I am using [this laptop](http://system76.com/product_info.php/cPath/1/products_id/181?osCsid=453c8a2a140261c7ec542d863d4fbffa).

---

### Post by mog27 on 2006-12-14
I am having this same exact problem too after doing the update today.  I'm glad I'm not alone.  

aplay -l
aplay: device_list:222: no soundcards found...


My sound and soundcard was working fine before the update. Anyone else have this issue?

I'm running a Dell Poweredge SC420.

---

### Post by Pobega on 2006-12-14
> **mog27 said:**
> I am having this same exact problem too after doing the update today.  I'm glad I'm not alone.  

aplay -l
aplay: device_list:222: no soundcards found...


My sound and soundcard was working fine before the update. Anyone else have this issue?

I'm running a Dell Poweredge SC420.

I'm happy to hear I'm not the only one with the problem, takes a load off of my shoulders.

Does anyone have any ideas what may be happening to our sound cards? I try everything I can find but I can't seem to save my old soundcard. 

If there is no solution found, is there any way to downgrade my Ubuntu install back to how it was yesterday?

---

### Post by essexman on 2006-12-14
same problem here - I have two sound cards and neith is detected.  The update was on my existing kernel 2.6.15-27-386 plus headers it was not a version update.

Very odd I'm going to see if I can undo until this is fixed

---

### Post by Pobega on 2006-12-14
Like I said, I did everything that [this thread](http://ubuntuforums.org/showthread.php?t=205449) said to do and nothing worked for me. So I'm not sure what's going on, but if it's not fixed in a few days I'm going to switch to Debian; I need to get my fix of Howard Stern

---

### Post by essexman on 2006-12-14
I Just installed the K7 kernel (being an Athlon user) and sound is back so this has to be the latest 2.6.17-27 kernel 386 (version 50 i think)

---

### Post by Pobega on 2006-12-14
I just tried to update my 686 kernel and it didn't help at all. Has anyone done anything else to remedy themselves of this problem?

**Edit:** Just installed 386 and the sound is now working, weird. Thanks Schthack for your patience and help :)

---

### Post by mog27 on 2006-12-14
Think this will be fixed in the next Ubuntu kernel update?  I can just wait till then if so.

---

### Post by Pobega on 2006-12-14
I'm hoping so, between this and the Nvidia problems Ubuntu really has to fix their kernel.

---

### Post by jgeewax on 2006-12-14
Could you elaborate (or give a post) on how you managed to fix this? (mentioned the 386 kernel....) for us newbies ofcourse :)

Thanks!


Update:   I just fixed it,
try 

sudo aptitude reinstall linux-image-`uname -r`

and then reboot. It worked for me!

---

### Post by mog27 on 2006-12-14
> **jgeewax said:**
> 

Update:   I just fixed it,
try 

sudo aptitude reinstall linux-image-`uname -r`

and then reboot. It worked for me!


Worked for me too!  Thanks.  I didn't know of such a command until now.

---

### Post by Pobega on 2006-12-15
That work with the 686 kernel? What does it do exactly?

---

### Post by martinquested on 2006-12-15
>  Originally Posted by jgeewax  View Post
[I]
Update: I just fixed it,
try

sudo aptitude reinstall linux-image-`uname -r`

and then reboot. It worked for me![/I]

Didn't work for me!

Do I have to do anything else?  I had installed the ALSA drivers manually, following the "Comprehensive Guide" on this forum...  is there something I need to do after that command?

Or should I just wait for them to correct and release a new kernel?

---

### Post by Pobega on 2006-12-15
Do you have an Athlon or an Intel processor?

---

### Post by martinquested on 2006-12-15
AMD Turion 64, in a Compaq Presario V6030US laptop, with an nVidia MCP51 audio card.

---

### Post by Pobega on 2006-12-16
Well [this is the thread](http://ubuntuforums.org/showthread.php?t=205449&highlight=Sound+Problem) I used to solve my problem, but I see nothing about your processor in there. 

There is a whole list of things you can try if you use *apt-cache search amd*, I'm not sure which will work for you though.

Good luck!

---

### Post by martinquested on 2006-12-17
For my happy ending, see [http://ubuntuforums.org/showpost.php?p=1897576&postcount=28](http://ubuntuforums.org/showpost.php?p=1897576&postcount=28)

---

### Post by Pobega on 2006-12-17
> **jgeewax said:**
> Could you elaborate (or give a post) on how you managed to fix this? (mentioned the 386 kernel....) for us newbies ofcourse :)

Thanks!


Update:   I just fixed it,
try 

sudo aptitude reinstall linux-image-`uname -r`

and then reboot. It worked for me!

Just jumped back on the 686 kernel, lost sound, installed that, restarted and sound came back!

But what's weird is I'm running Ubuntu and when I was restarting it said "Kubuntu". I wonder if I messed something up.

---

