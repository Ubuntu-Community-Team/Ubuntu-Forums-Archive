---
title: "Updating Ubuntu &amp; Firefox to newest version"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by deank77 on 2007-03-17
Hi,

I am very new to Linux. I bought The Official Ubuntu Book, and it comes with the Ubuntu 6.06LTS, and Firefox 1.5.  

I want update the browser to Firefox 2.0.0.2. How do I go about in doing that?

Next, how do I upgrade to Ubuntu 6.10?  


A step-by-step guide is most appreciative.

Thank you very much.

cheers,
Dean  :popcorn:

---

### Post by qamelian on 2007-03-17
You'll find everything you need right here:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by jbayone on 2007-03-17
[http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox")

---

### Post by loanrangie on 2007-03-17
> **deank77 said:**
> Hi,

I am very new to Linux. I bought The Official Ubuntu Book, and it comes with the Ubuntu 6.06LTS, and Firefox 1.5.  

I want update the browser to Firefox 2.0.0.2. How do I go about in doing that?

Next, how do I upgrade to Ubuntu 6.10?  


A step-by-step guide is most appreciative.

Thank you very much.

cheers,
Dean  :popcorn:

 If you go into Firefox >tools>options >advanced > update , and tick the box marked automtically download and install updates it will upgrade next time you restart it.

---

### Post by deank77 on 2007-03-17
Thank you for your replies! This will, hopefully, make my adjustment to Linux OS much easier. Very appreciated.

Thanks   :)

---

### Post by aysiu on 2007-03-17
> **loanrangie said:**
> If you go into Firefox >tools>options >advanced > update , and tick the box marked automtically download and install updates it will upgrade next time you restart it.
Um, that won't work. The latest version of Firefox in Dapper is 1.5, not 2.0.

This is what you need:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by mr_ed on 2007-03-17
> **loanrangie said:**
> If you go into Firefox >tools>options >advanced > update , and tick the box marked automtically download and install updates it will upgrade next time you restart it.

That may be there in Windows, but not in Ubuntu.  Under Edit>Preferences>Advanced>Update, the Firefox update is grayed out.
The easiest way to do it is upgrade to Edgy like a previous poster has pointed out.

EDIT:  Hmm... I guess I had this page open for a while before posting.  **aysiu**, you beat me to it.  ;)

---

### Post by aysiu on 2007-03-17
> **mr_ed said:**
> 
The easiest way to do it is upgrade to Edgy like a previous poster has pointed out. I wouldn't call that the *easiest* way. I'd call that *a* way.

The easiest way is to use the script I linked to above.

A) Upgrade one program (Firefox) with a simple script
B) Upgrade the entire operating system (including Firefox)

I'd say A is the easiest.

---

### Post by Pragmatik on 2007-03-27
That script from psychocats worked like a charm.  Thanks to all who posted it and wrote it, too:)

---

### Post by vgrisham on 2007-03-28
I used aisyu's script from the psychocats website, and I've been happily sailing along with Firefox 2 and Dapper for a couple of months now. (Now if someone would only create such a script for Exaile and Dapper...)

I have a two related questions. First, this morning, Synaptic started prompting me to upgrade--to a newer version of 1.5. Of course, I don't want to go back to 1.5, so is there a way to tell Synaptic to NOT prompt me to upgrade Firefox anymore? 

Second, how do I go about updating Firefox 2 as new releases come available. Do I simply use the psychocats script again? (Ideally, I'll be moving to Feisty, but there are some unfortunate snags related to my Atheros 5212 wireless card that may prevent me from doing so anytime soon. As long as I can keep stringing along my Dapper programs, I'm in no rush.).

Thanks for your help.

Vaughn

---

### Post by NeoGreen on 2007-03-28
Outstanding thread.  I was about to post something similar.  Thanks.  :)

---

### Post by scrooge_74 on 2007-03-28
> **vgrisham said:**
> I used aisyu's script from the psychocats website, and I've been happily sailing along with Firefox 2 and Dapper for a couple of months now. (Now if someone would only create such a script for Exaile and Dapper...)

I have a two related questions. First, this morning, Synaptic started prompting me to upgrade--to a newer version of 1.5. Of course, I don't want to go back to 1.5, so is there a way to tell Synaptic to NOT prompt me to upgrade Firefox anymore? 

Second, how do I go about updating Firefox 2 as new releases come available. Do I simply use the psychocats script again? (Ideally, I'll be moving to Feisty, but there are some unfortunate snags related to my Atheros 5212 wireless card that may prevent me from doing so anytime soon. As long as I can keep stringing along my Dapper programs, I'm in no rush.).

Thanks for your help.

Vaughn

You can tell synaptic to freeze a package so it does not update it any more, after selecting the package go to the options on the top bar and freeze it

---

### Post by halitech on 2007-03-28
I'm using 6.06 and I don't have a freeze option. Would it be the same as going Package -> Lock version?

---

### Post by aysiu on 2007-03-28
> **halitech said:**
> I'm using 6.06 and I don't have a freeze option. Would it be the same as going Package -> Lock version? Yes, that's how you do it.

> **vgrisham said:**
> 
I have a two related questions. First, this morning, Synaptic started prompting me to upgrade--to a newer version of 1.5. Of course, I don't want to go back to 1.5, so is there a way to tell Synaptic to NOT prompt me to upgrade Firefox anymore?  You wouldn't actually be going *back* to 1.5. 1.5 is already installed and lives separately from the 2.0 the script installed. To launch 2.0, you use the command *firefox*. To use 1.5, you use the command *firefox.ubuntu*. As halitech points out, if you want to stop receiving updates to 1.5, you can go to Synaptic > Package > Lock Version.

> Second, how do I go about updating Firefox 2 as new releases come available. Do I simply use the psychocats script again? (Ideally, I'll be moving to Feisty, but there are some unfortunate snags related to my Atheros 5212 wireless card that may prevent me from doing so anytime soon. As long as I can keep stringing along my Dapper programs, I'm in no rush.). Close Firefox. Press Alt-F2. Type ```
gksudo firefox
``` Go to Help > Check for Updates. Install the updates. Restart Firefox when prompted. Close Firefox. Restart Firefox normally.

---

### Post by vgrisham on 2007-03-28
Thanks very much for the help. I got the package locked, and I even updated Firefox 2 using the gksudo firefox command. :guitar:

---

### Post by digbysellers on 2007-03-29
Thank you. This was extremely helpful!

---

### Post by david_kt on 2007-03-29
> **aysiu said:**
> I wouldn't call that the *easiest* way. I'd call that *a* way.

The easiest way is to use the script I linked to above.

A) Upgrade one program (Firefox) with a simple script
B) Upgrade the entire operating system (including Firefox)

I'd say A is the easiest.

Recently I tried that script (I downloaded a few months ago), but this time it did not work. It stop at choosing language, there was no option given, and entering any number was also did not work. What I did was I remove the downloading script, and download it manually and put it on my home folder. Other part of the script worked well.

Do you update the script recently? Or may be just the network connection problem at that time? Anyway, I managed to use it after I modified it. I just concern if this is permanent problem, not network connection problem. I connect to internet through MS ISA, using NTLMAPS.

DK

---

### Post by aysiu on 2007-03-29
I actually didn't write the script. *nanotube* (another forum member) did, and I did some testing on it and gave some feedback for improvement. All the coding is by *nanotube*, and I don't believe it has been updated recently (but it should always pull the latest Firefox from Mozilla).

---

### Post by david_kt on 2007-03-29
Right, it is still able to detect the latest version, but fail to capture the download location. From the script, I was able to trace the download location manually, and put it in the right folder manually (home folder). After that, I remove downloading script, and run the script again without any error.

DK

---

### Post by LeeU on 2007-03-30
> **aysiu said:**
> Close Firefox. Press Alt-F2. Type ```
gksudo firefox
``` Go to Help > Check for Updates. Install the updates. Restart Firefox when prompted. Close Firefox. Restart Firefox normally.

You might want to add this to the page with the script (thanks, BTW!). Otherwise it's a bit confusing when the update is grayed out.

---

### Post by aysiu on 2007-03-30
Yeah, I'll update the page to say that (some time in the next day or two).

---

