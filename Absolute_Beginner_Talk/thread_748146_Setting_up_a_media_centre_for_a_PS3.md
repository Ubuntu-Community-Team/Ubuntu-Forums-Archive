---
title: "Setting up a media centre for a PS3"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by CheeseEatingBulldog on 2008-04-07
Hello all, 
I just got a ps3 from my lovely gf, and in the same week she seems to have fried my svideo out on my video card by plugging wrong cables in to wrong holes, anyway the ps3 has wifi and has the option of connecting to a media server, which would surcumvent the whole cable issue, if I knew how to set it up on my ubuntu install.

I read that things like mythtv are such apps and wondered how to go about this, is it as easy as apt-getting and setting up mythtv to share my video folders? Can I then browse my machine and watch movies from my desktop harddrive?

Thanks in advance,

---

### Post by R6V2 on 2008-04-07
If you got wireless internet, go ahead and hook up your PS3 through the internet, and you can access your files via your computer.

If your computer has wifi/bluetooth connect directly to it! :)

---

### Post by aeiah on 2008-04-07
if you're just wanting to set up an UPnP media server then mythtv is probably overkill. check out mediatomb. it'll run in the background when ubuntu is running and share your media over the network. i think it has problems with sharing HD content (and wifi probably wont provide enough bandwidth for it anyway) but everything else should be fine. HD isnt impossible, but might be tricky.

check this:

[http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me](http://www.freesoftwaremagazine.com/columns/upnp_mediatomb_ps3_and_me)

---

### Post by Chemist on 2008-04-07
do you know if mediatomb will share media with xbox360??

I've been having trouble streaming my vids through it :(

---

### Post by jkeyes0 on 2008-04-07
> **Chemist said:**
> do you know if mediatomb will share media with xbox360??

I've been having trouble streaming my vids through it :(

I use ushare from GeeXbox to share my media to my xbox 360.
[http://ushare.geexbox.org/](http://ushare.geexbox.org/)
[http://sourceforge.net/projects/ushare](http://sourceforge.net/projects/ushare)

---

### Post by Chemist on 2008-04-07
i've been struggling to get ushare working, various dependacies are missing. rather than highjack this one. I'll start new when I get home :)

thanks for the advice though mate

---

### Post by CheeseEatingBulldog on 2008-04-07
Thanks for the replies, ubuntuforums are as usual  very helpful, will try out the mediatomb when I get in tonight. Wireless would be a lot easier.

Cheers!

---

### Post by CheeseEatingBulldog on 2008-04-08
Right, I got mediatomb running...but...well when I burn my .avi files to a disc and put it in my ps3 it plays the files, however when browsing to those same files via media server it comes up with unsuupported media type...WTF? We are talking the exact same files.

Any ideas?

---

### Post by Mick8882003 on 2008-04-08
seperate question, how hard would it be to set up a dedicated media center based on ubuntu, is there a distro for it???

---

### Post by CheeseEatingBulldog on 2008-04-08
Mythtv seems to be a dedicated media server. Check it out, and as for the files types, I think I have found a sollution in [http://ubuntuforums.org/showthread.php?t=648582]("http://ubuntuforums.org/showthread.php?t=648582")

---From above thread----

1) Edit the MediaTomb configuration file (/etc/mediatomb/config.xml) to set a suitable mime types for .avi and .vob file types. My section of this file now looks like this:

<mappings>
<extension-mimetype ignore-unknown="no">
<map from="avi" to="video/x-divx"/>
<map from="vob" to="video/mpeg"/>
<map from="mp3" to="audio/mpeg"/>
<map from="ogg" to="application/ogg"/>
<map from="asf" to="video/x-ms-asf"/>
<map from="asx" to="video/x-ms-asf"/>
<map from="wma" to="audio/x-ms-wma"/>
<map from="wax" to="audio/x-ms-wax"/>
<map from="wmv" to="video/x-ms-wmv"/>
<map from="wvx" to="video/x-ms-wvx"/>
<map from="wm" to="video/x-ms-wm"/>
<map from="wmx" to="video/x-ms-wmx"/>
<map from="m3u" to="audio/x-mpegurl"/>
<map from="pls" to="audio/x-scpls"/>
</extension-mimetype>

(2) Delete MediaTomb's database file (/var/lib/mediatomb/sqlite3.db) or the changes to the config file above wont do anything. You will have to re-add you files to MediaTomb later.

(3) Restart MediaTomb. I reboot my PC to achieve this.

(4) Re-add your media files files to MediaTomb in the usual way with the HTML interface.

(5) Ensure your PS3 has at least version 2.10 of the firmware installed.

(6) Re-boot your PS3 (or just select 'search for media servers') to ensure it has not cached the details of you media files.

That is it, your PS3 should be able to play streamed .avi files and .vob files.

------end-----

Will give this a try tonight when I get in.

---

### Post by aeiah on 2008-04-08
> **Mick8882003 said:**
> seperate question, how hard would it be to set up a dedicated media center based on ubuntu, is there a distro for it???

yea there's mythbuntu, but it really depends on what you want to do. i have my pc connected to my HDTV in my livingroom. i dont bother with any media center interface because i find it more convenient to just click my big film folder icon on the desktop and navigate to what i want, or use elisa for music.

i have looked into elisa and xbmc to see what they offer and whilst both are nice, they still arent as convenient. i suppose if you're using a remote control and not a wireless mouse and keyboard then they'd be good though. if you want tv recording functionality, you deffinatley want to go for mythtv id say. other than that, there are several interfaces for just playing videos and music. just set them to autostart on boot over the top of something like fluxbuntu

---

### Post by HornedBeast on 2008-04-30
I have written this guide for this exact purpose. Hopefully you will find it useful.

It was written with the Xbox 360 in mind, but TwonkyMedia (the software used) should happily stream to the PS3 as well (its part of their spec).

Hope it helps.

[http://ubuntuforums.org/showthread.php?t=775906](http://ubuntuforums.org/showthread.php?t=775906)

HornedBeast

---

