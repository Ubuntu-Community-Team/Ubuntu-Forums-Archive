---
title: "We could really use a mod that would make a couple Stickies."
date: 2007-06-21
forum: Apple Intel Users
---

### Post by Gen2ly on 2007-06-21
Just to help simplify things a bit, a couple stickies would be nice.  I notice a fair number of posts are duplicates or just end up pointing to the wiki or what not.

First we need a post that details specific MacBook installation instructions.  This will point to the MacBook wiki.  You could use the original one since some are still posting to it (though the title will have to be renamed):

[**[COLOR="Sienna"]How to install Ubuntu 6.10 "Edgy Eft" on a MacBook[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=290710")

Also the Compile the Kernel thread since it has specific instructions related to the mactel patches:

[**[COLOR="Sienna"]HOWTO: Compile a Kernel for your MacBook[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=442941")

---

### Post by ivesjd on 2007-06-21
I agree, there are many threads that keep coming up every week or so.

---

### Post by ronocdh on 2007-06-21
> **ivesjd said:**
> I agree, there are many threads that keep coming up every week or so.
A nice MadWiFi one would be very useful. I often link to [this one]("http://ubuntuforums.org/showthread.php?t=429641"). Do you guys know any better ones? Also, both links in my sig I think are worth making stickies out of, as the X failure happens to everyone with the ATI card. We could use one for resolving the splash screen boot hang in the SR MBPs, but I don't understand that issue very well.

---

### Post by ronocdh on 2007-06-22
Here's an excellent how-to for getting rid of the splash screen boot error on the Santa Rosa MBPs: [http://ubuntuforums.org/showpost.php?p=2892053&postcount=10](http://ubuntuforums.org/showpost.php?p=2892053&postcount=10)

---

### Post by Gen2ly on 2007-06-22
[[COLOR="Sienna"]**Benanzo's post**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2731459&postcount=25") might be usefull for madwifi too.  I imagine we won't need it for long though, the madwifi drivers seem much better nowdays.

---

### Post by ivesjd on 2007-06-24
How do we go about getting stickies made?

---

### Post by ~joe~ on 2007-06-24
Those threads are excellent; I second (third?) the suggestion of making these into stickies.

> **ivesjd said:**
> How do we go about getting stickies made?
I admit that I'm extremely new to this forum, but I'd recommend PM'ing a moderator or a super-mod. Ideally, someone who's familiar with Macs.

---

### Post by ronocdh on 2007-06-24
> **~joe~ said:**
> Those threads are excellent; I second (third?) the suggestion of making these into stickies.


I admit that I'm extremely new to this forum, but I'd recommend PM'ing a moderator or a super-mod. Ideally, someone who's familiar with Macs.
Actually I did just PM a mod. I was worried it'd be perceived as rude, but hopefully click and so what helpful community members we're being by building a list. :D Hat tip to Dirk for starting the thread.

---

### Post by Gen2ly on 2007-06-25
Did you hear anything from a mod, rono?  if not, I can contact darkmatter, I think he will do it.  I've seen him here before in these forums.

---

### Post by ronocdh on 2007-06-25
> **Dirk.R.Gently said:**
> Did you hear anything from a mod, rono?  if not, I can contact darkmatter, I think he will do it.  I've seen him here before in these forums.
Nothing yet. I messaged ubuntu_demon. Tseliot was my second choice. If you've seen Darkmatter here, all the better. Hit it up.

---

### Post by ronocdh on 2007-06-26
> **ronocdh said:**
> Nothing yet. I messaged ubuntu_demon. Tseliot was my second choice. If you've seen Darkmatter here, all the better. Hit it up.
Heard back. Ubuntu_demon recommends we compile a list of threads into a single sticky, and gave [this example]("http://ubuntuforums.org/showthread.php?t=232037").

I thought I'd add [this]("http://ubuntuforums.org/showpost.php?p=2917086&postcount=22") to our list. Once we cover ever thing, we'll make a sticky and submit that to mods. What else do we need? I think our MadWifi could be phrased better, but maybe it's a simpler process these days.

---

### Post by ~joe~ on 2007-06-26
> **ronocdh said:**
> I think our MadWifi could be phrased better, but maybe it's a simpler process these days.
It should be, just look at this Debian MacBook wiki guide:
[http://wiki.debian.org/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](http://wiki.debian.org/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)
> Add 'non-free' to your main Debian repository then update your packages list with

```
aptitude update

```Install the madwifi kernel module source and the ability to compile it

```
aptitude install madwifi-source madwifi-tools module-assistant

```Compile it

```
m-a prepare
m-a a-i madwifi
depmod -a
modprobe ath_pci
```
I mean, you'd have to use the Debian repositories (it doesn't appear that the madwifi source is available from Ubuntu), but don't you think it'd make it significantly easier to install? This method worked excellent for me on Debian.

And another thing, isn't it weird that madiwifi can't be installed directly from the LiveCD? I find it odd because the LiveCD of Ubuntu loads up madwifi automatically on my MacBook and I can surf the internet with it.

---

### Post by Gen2ly on 2007-06-27
Yeah rono, I think those two first threads mentioned (the wiki and the kernel) and a wifi one would be nice as well.  I can't really think of anything else unless you wanna include a mention to Anna Nicole. :P

---

### Post by Gen2ly on 2007-06-29
rono, are you writing this up?  do you want me to do it?

---

### Post by cyberdork33 on 2007-06-29
Another thing we should probably post is bluetooth setup...
I found this today:
[http://ubuntuforums.org/showthread.php?t=432013&highlight=bluetooth+how+to](http://ubuntuforums.org/showthread.php?t=432013&highlight=bluetooth+how+to)

I had found a really good guide previously and have lost it. I will keep looking.

---

### Post by ronocdh on 2007-06-29
> **cyberdork33 said:**
> Another thing we should probably post is bluetooth setup...
I found this today:
[http://ubuntuforums.org/showthread.php?t=432013&highlight=bluetooth+how+to](http://ubuntuforums.org/showthread.php?t=432013&highlight=bluetooth+how+to)

I had found a really good guide previously and have lost it. I will keep looking.
Killer! Sticky it!

Dirk, you started the thread, so give it a go. We'll all critique on the format and stuff until it's good enough to send to a mod. I'm headed out for the day today but will check bck tomorrow, and I guess make a draft if you haven't by that point.

GL!

---

### Post by Gen2ly on 2007-06-29
> **ronocdh said:**
> Killer! Sticky it!
Sure, I can do it.
> Dirk, you started the thread, so give it a go. We'll all critique on the format...
Lucky me.
> ...and I guess make a draft if you haven't by that point.

I'll probably have an opportunity to do this, I hope, today.

---

### Post by alephsmith on 2007-07-01
As a new owner of a SR Macbook Pro I look forward to having a sticky here for easy access to some instructions.

Thanks for your effort in putting all this together guys. I may just pick up the courage to try and install this thing :p

---

### Post by Gen2ly on 2007-07-01
The information I think that is needed:

**[COLOR="DarkRed"]Posts useful to intel-Mac owners.[/COLOR]**

If you have a question, then a fair number of the forum users are very willing to help, don't be afriad to ask.  Likewise, alot of answers can also be found here.  Also it is requested you search what topic you concerned with and try not to replicate threads.

The MacBook Ubuntu Wiki - covers details of installing Ubuntu on a MacBook.  First time users best start at the wiki.

[**[COLOR="Sienna"]How to install Ubuntu 6.10 "Edgy Eft" on a MacBook[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=290710")

More advanced users may wish to compile their own kernel.  This provides advantages over general kernels that can be a bit slower, and not as nicely tuned to your system.

[**[COLOR="Sienna"]HOWTO: Compile a Kernel for your MacBook[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=442941")


Posts that I'm not sure about - Iffy's

**Santa Rosa**

[LIST]
[*][**[COLOR="Sienna"]getting rid of the splash screen boot error on the Santa Rosa MBP[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=2892053&postcount=10")

[*][**[COLOR="Sienna"]Instructions on how to get a graphical install of Ubuntu on a Santa Rosa MBP[/COLOR]**]("http://ubuntuforums.org/showpost.php?p=2917086&postcount=22")
[*]	Maybe the wiki would be a better place for these?
[/LIST]
**Audio Distortion** - seems to me we saw a thread of this, but enough users having this issue?.

**Some madwifi ones**:
[LIST]
[*][[COLOR="Sienna"]**HOWTO: Installing Madwifi drivers**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=485579") 
[*][[COLOR="Sienna"]**Benanzo's post**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2731459&postcount=25")
[/LIST]

**Bluetooth** - is this the same bluetooth in MacBooks?

[LIST]
[*][[COLOR="Sienna"]**HOW TO: Logitech MX5000 via (bluetooth)**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=432013&highlight=bluetooth+how+to")
[/LIST]

Also, a reasonable question.  rono could you ask if this thread will be editable?  If not we better not have date-sensitive material.  Did I miss any?

---

### Post by cyberdork33 on 2007-07-01
Here is the community help page on bluetooth (wiki):
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

The process is the same on all machines as far as I can tell. I thought it would be helpful to some since many may have wireless keyboards / mice they want to use. Maybe this and the kernel thread can be in a 'general' section (not mac specific) since they would essentially cover any machine, although from a Mac standpoint.

I think whomever writes the thread starting post can edit the information inside.

Did we get a touchpad config guide? A lot of this could be put in the wiki too, then it would editable by several.

---

### Post by ivesjd on 2007-07-01
An iSight set-up would very nice as well, [This ]("http://ubuntuforums.org/showthread.php?t=225621") one is good but some people seem to think that you need to do the whole thing and mount the mac partition. With the top part you don't. I could rewrite it, just didnt want to make even more iSight related threads.

---

### Post by cyberdork33 on 2007-07-02
> **ivesjd said:**
> An iSight set-up would very nice as well, [This ]("http://ubuntuforums.org/showthread.php?t=225621") one is good but some people seem to think that you need to do the whole thing and mount the mac partition. With the top part you don't. I could rewrite it, just didnt want to make even more iSight related threads.

I pm'd rapido and asked him to add some clarification to his How To.

---

### Post by ronocdh on 2007-07-02
I do think distorted audio should be mentioned. Try these three links (and evaluate which are necessary):
[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=371047](http://ubuntuforums.org/showthread.php?t=371047)
[*][http://ubuntuforums.org/showthread.php?t=420909](http://ubuntuforums.org/showthread.php?t=420909)
[*][http://ubuntuforums.org/showthread.php?t=489700&highlight=distorted+audio](http://ubuntuforums.org/showthread.php?t=489700&highlight=distorted+audio)
[/LIST]
Also, "afraid" is misspelled in the beginning of the post. Looking excellent! I do not know whether it'll be editable... does anyone even know the regular cut-off time for editing posts?

*Edit: FWIW, I am given the option to edit my April 24, 2007 post on one of those audio threads... that's over 2 months! I don't know whether stickies are special in being uneditable, though. Anyone?*

---

### Post by Gen2ly on 2007-07-02
> **cyberdork33 said:**
> Here is the community help page on bluetooth (wiki):

Did we get a touchpad config guide? A lot of this could be put in the wiki too, then it would editable by several.


I think the touchpad config is a good idea.  A link or on wiki would be nice.   Where are the details for it? - There are a fair number of settings.  

[**[COLOR="Sienna"]Bluetooth Setup[/COLOR]**](https://help.ubuntu.com/community/BluetoothSetup)

[HOWTO iSight]("http://ubuntuforums.org/showthread.php?t=225621")
nice , i like it.

Thread to audio problems:

   1. [http://ubuntuforums.org/showthread.php?t=371047](http://ubuntuforums.org/showthread.php?t=371047)
   2. [http://ubuntuforums.org/showthread.php?t=420909](http://ubuntuforums.org/showthread.php?t=420909)

Ok, do the last details on the post later tonight maybe, or tomorrow.

---

### Post by cyberdork33 on 2007-07-02
can't help you there. no touchpad. I would just say 'man synaptics'

---

### Post by Gen2ly on 2007-07-03
> **ivesjd said:**
> An iSight set-up would very nice as well, [This ]("http://ubuntuforums.org/showthread.php?t=225621") one is good but some people seem to think that you need to do the whole thing and mount the mac partition. With the top part you don't. I could rewrite it, just didnt want to make even more iSight related threads.

If like to do it ivesjd it would be nice but I'd like to have this sticky up in a couple days.

Ok, here it is: 

Final Draft!!?
---------------------------------------------------------

If you have a question, feel free to ask it in the forums - a fair number of forum users are very willing to help.  Likewise, alot of answers can also be found here.  To help avoid replicate threads it is requested to search the topic concerned before posting a new topic.


**[COLOR="DarkRed"][SIZE="4"]Posts Useful to intel-Mac owners.[/SIZE][/COLOR]**


[**[COLOR="Sienna"]The MacBook Ubuntu Wiki[/COLOR]**]("https://help.ubuntu.com/community/MacBook")
[LIST]
[*]Covers details of installing Ubuntu on a MacBook.  First time users best start at the wiki.
[/LIST]
[**[COLOR="Sienna"]Bluetooth Setup[/COLOR]**](https://help.ubuntu.com/community/BluetoothSetup)
[LIST]
[*]If you use a short-distance wireless device this has some nice information.
[/LIST]
[**[COLOR="Sienna"]HOWTO iSight[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=225621")
[LIST]
[*]an iSight HowTo
[/LIST]
[[COLOR="Sienna"]**HOWTO: Installing Madwifi drivers**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=485579")
[LIST]
[*]Install the madwifi drivers the Ubuntu way.
[/LIST]

**Advanced Posts**

[**[COLOR="Sienna"]HOWTO: Compile a Kernel for your MacBook[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=442941")
[LIST]
[*]More advanced users can to compile their own kernel.  This provides advantages over general kernels that can be a bit slower, and not as nicely tuned to your system.
[/LIST]
[[COLOR="Sienna"]**Benanzo's post on Howto Compile Madwifi Drivers**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2731459&postcount=25")
[LIST]
[*]Compile the madwifi drivers from scratch.
[/LIST]

---------------------------------------------------------------------------------------------------

I'm not planning to put in audio details or touchpad since there isn't a howto for them,  nor do I plan to include any date-sensitive detail.

Also, I think [getting rid of the splash screen boot error on the Santa Rosa MBP]("http://ubuntuforums.org/showpost.php?p=2892053&postcount=10") and [Instructions on how to get a graphical install of Ubuntu on a Santa Rosa MBP]("http://ubuntuforums.org/showpost.php?p=2917086&postcount=22") are best put in the wiki.

---

### Post by ivesjd on 2007-07-03
I made a new iSight how-to that is more clear I think. If anyone has any suggestions, just pm me and I'll change it.

[http://ubuntuforums.org/showthread.php?p=2957042#post2957042](http://ubuntuforums.org/showthread.php?p=2957042#post2957042)

---

### Post by Gen2ly on 2007-07-03
Very nice, ivesjd.  I used your thread in the Howto iSight.  Ok here's the thread in all it's splendor.

---

### Post by ronocdh on 2007-07-04
We need a thread for ndiswrapper for the Broadcom chipsets. And make it explicit in the sticky that MadWifi is only for Atheros users (tell them to run **sudo update-pciids** and **lspci** to determine their wireless hardware).

---

### Post by cyberdork33 on 2007-07-04
Yea I just got  a PM about doing this.

here is the ndiswrapper page in the wiki:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

Here is a simple one for bcm43xx:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28bcm43xx%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28bcm43xx%29)

---

### Post by ronocdh on 2007-07-04
> **cyberdork33 said:**
> Yea I just got  a PM about doing this.

here is the ndiswrapper page in the wiki:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

Here is a simple one for bcm43xx:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28bcm43xx%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff?highlight=%28bcm43xx%29)
Thumbs up to the links, but Dirk, just remember to remove the highlight strings from the end of the URLs. ;)

Also, on the subject of maintenance, there's [this sticky]("http://ubuntuforums.org/showthread.php?t=368607") in the 64-bit forums; it was created in February and last edited just last week. So should be good to go! We'll just have to remember to hound Dirk whenever a change is needed. ;)

---

### Post by cyberdork33 on 2007-07-04
> **ronocdh said:**
> Thumbs up to the links, but Dirk, just remember to remove the highlight strings from the end of the URLs. ;)

Also, on the subject of maintenance, there's [this sticky]("http://ubuntuforums.org/showthread.php?t=368607") in the 64-bit forums; it was created in February and last edited just last week. So should be good to go! We'll just have to remember to hound Dirk whenever a change is needed. ;)

Oops!

and yea the 64-bit question is a good one to have an answer to

---

### Post by tseliot on 2007-07-05
Ok, I have made a sticky thread by moving one of Dirk.R.Gently's posts so that he can edit the thread and maintain it:
[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)

Should you have further suggestions, please let me know.

Regards

Alberto

---

### Post by cyberdork33 on 2007-07-05
Yay

---

