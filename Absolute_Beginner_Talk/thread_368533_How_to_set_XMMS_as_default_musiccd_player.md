---
title: "How to set XMMS as default music/cd player?"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by l0k1_ on 2007-02-23
Is there a way to make xmms automatically play my audio cds? Right now all that pops up is sound juicer, can I get rid of this too? thanks.

---

### Post by Obor on 2007-02-23
I think if you navigate into your cd in Nautilus (file browser) right click on one of the songs and go into properties - open with - and choose xmms from the list it should play all files with the same file extension in xmms.

---

### Post by tipping point on 2007-02-23
Apparently this is not as easy as one would think it should be, we need some serious step by step directions to accomplish this. I was just online Ubuntu(XChat) with someone who tried to walk me thru but I still have that SoundJuicer and no XMMS. I cant get any songs from CD in XMMS playlist even after fooling with cd mount and media/cdrom nothing worked.

---

### Post by l0k1_ on 2007-02-24
Yeah, even right now I have no idea how to play audio cd's in XMMS. Theres no option to do that, or I haven't been able to find one.

---

### Post by yabbadabbadont on 2007-02-24
Try installing the xmms-cdread plugin.  It will let xmms play audio cds in drives that don't have an audio cable connecting them to the soundcard.

sudo apt-get install xmms-cdread

Then be sure to check the plugin preferences in the xmms preferences menu.

---

### Post by tipping point on 2007-02-24
My CD player is connected to my soundcard, when I go to Preferences-Input plugins and highlight CD Audio Player -configure - Device - Drive 1-check drive - I get "Failed To Read Table of Contents" Maybe no disc in Drive. Of course theres a disc in drive, thats the problem its not reading the songs on the CD to load in playlist. Online at Ubuntu Xchat said XMMS should be listed in the Input plugins preferences, should it ?

---

### Post by tipping point on 2007-02-25
OK found something, got XMMS working follow directions at this link, [http://facilities.cs.utexas.edu/htdoc/faqs/multimedia.html](http://facilities.cs.utexas.edu/htdoc/faqs/multimedia.html) . This works perfectly insert CD and XMMS loads just add songs from Play files to playlist  and you're jamming.

---

### Post by tommyp on 2007-03-27
In gnome,  you can control what program opens by going to:

System>Preferences>Removable Drives and Media and going to the multimedia tab

---

### Post by Vonko on 2007-04-11
Thank you for the post, I have the same problem. I went to System > Preferences > removable drives and media, BUT the only one listed is the one I do not want. It does shows a BROWSE button, but I would not know where to find the "exe" for XMMS. Please help

---

### Post by Obor on 2007-04-11
> **Vonko said:**
> Thank you for the post, I have the same problem. I went to System > Preferences > removable drives and media, BUT the only one listed is the one I do not want. It does shows a BROWSE button, but I would not know where to find the "exe" for XMMS. Please help

it should be in  /usr/bin/xmms 
if you type 'whereis xmms' (without quotes) in the terminal it will find it for you.

---

### Post by Vonko on 2007-04-11
Thank you. I really don't know what I am looking for.. What is the "exe" called and is there one location for it?. I want XMMS to play my shoutcast radios (URL's) automatically. The path I described above does not help this, or does it? Please help

---

### Post by Vonko on 2007-04-11
I found a solution by using Firefox ad-on 
MediaPlayerConnectivity 0.8.3 
by Sethnakht , it is great help for newbies like me. I allows to switch between players, setting them as default for different activities.
Case closed for me.

---

### Post by homerj742 on 2007-04-14
> **Vonko said:**
> I found a solution by using Firefox ad-on 
MediaPlayerConnectivity 0.8.3 
by Sethnakht , it is great help for newbies like me. I allows to switch between players, setting them as default for different activities.
Case closed for me.

Where would I get this? I'm having the same issue.

---

