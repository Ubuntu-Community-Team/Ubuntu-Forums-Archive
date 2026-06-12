---
title: "How to I get embeded midi to play in Firefox browser!"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by XeroCurve on 2006-07-26
**This is what im running:**

Dapper (Upgraded from Breezy)

**This is what ive done so far:**

Installed Automatix
[LIST]
[*](Changed things but no midi)
[*](Used this thread --> [http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025))
[/LIST]

Installed Media Connectivity
[LIST]
[*](Partially worked but not the way it needs to be)
[/LIST]

Installed EasyUbuntu
[LIST]
[*](Stated that it couldnt apply changes and that I needed to fix broken packages)
[/LIST]

Changed my Web Pages to <object> tags instead of <embed>
[LIST]
[*](No difference)
[/LIST]

Searched through files
[LIST]
[*](The correct plugins show up in /usr/lib/firefox/plugins but they are not in /opt/firefox/plugins)
[/LIST]

Did **about: plugins** in Firefox
[LIST]
[*](List does not include the mplayer plugins)
[/LIST]

Is there a possibility that something is corrupted and I maybe need to just reinstall from the ground up?

Sincerly Wits End.

---

### Post by XeroCurve on 2006-07-26
One quick note for gee wiz knowledge. I did get the embeded midi to play in Firefox on a Windows box when I changed the <embed> tags into <object> tags. 

This doesnt change what this thread is about but it may help someone..

Here is the code:

```
<object data="gra-coin.mid" type="audio/midi">
	<param name="AutoStart" value="true">
	<param name="loop" value="true">
</object> 
```

Instead of:

```
<embed src="gra-coin.mid" hidden autostart="4">
```

---

### Post by nalmeth on 2006-07-26
Open up a terminal and go:
sudo apt-get install mozilla-mplayer

---

### Post by XeroCurve on 2006-07-26
It states that its the newest version already and changes 0 items.

---

### Post by avtolle on 2006-07-26
A perhaps not too good suggestion: install Wine, run FF under Wine, get the embedded midi to play as you did in Windows.

---

### Post by XeroCurve on 2006-07-26
No offense but I dont want to run anything in Wine if at all possible =)

---

### Post by klytu on 2006-07-26
> **XeroCurve said:**
> **This is what im running:**

Dapper (Upgraded from Breezy)

**This is what ive done so far:**

Installed Automatix
[LIST]
[*](Changed things but no midi)
[*](Used this thread --> [http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025))
[/LIST]

Installed Media Connectivity
[LIST]
[*](Partially worked but not the way it needs to be)
[/LIST]

Installed EasyUbuntu
[LIST]
[*](Stated that it couldnt apply changes and that I needed to fix broken packages)
[/LIST]

Changed my Web Pages to <object> tags instead of <embed>
[LIST]
[*](No difference)
[/LIST]

Searched through files
[LIST]
[*](The correct plugins show up in /usr/lib/firefox/plugins but they are not in /opt/firefox/plugins)
[/LIST]

Did **about: plugins** in Firefox
[LIST]
[*](List does not include the mplayer plugins)
[/LIST]

Is there a possibility that something is corrupted and I maybe need to just reinstall from the ground up?

Sincerly Wits End.

I feel your pain! I have been there myself. I don't know how much I'll be able to help but I'll give it a shot. Can you please post the output of the following:

```
which firefox
```

also do:

```
sudo updatedb
```

let that finish, then:

```
locate plugins
```

Also, I am assuming from your frustration that it is not just a specific web site that you can't play embedded midi from? Or no embedded midi plays at all? Can you play embedded video? Can you play midi/video outside of firefox?

---

### Post by XeroCurve on 2006-07-26
Yes I can play midi in an app called "Timidity" and they play fine. I can also play online radio stations with "xmms", but I cant play any embeded midi in any sites.

---

### Post by klytu on 2006-07-26
> **XeroCurve said:**
> Yes I can play midi in an app called "Timidity" and they play fine. I can also play online radio stations with "xmms", but I cant play any embeded midi in any sites.

OK. Could you post the output of the commands I suggested in the previous post? More specifically the outputs of 

```
which firefox
```

and 

```
locate plugins
```

after you run updatedb. If the output of "locate plugins" is really long, you can direct the output to a file like this, for example:

```
locate plugins > plugs
```

which will save the information in the file "plugs". Then you can attach the file to your post. What I intend to try is to find out what plugins you actually have installed and then get them in the proper place according to where firefox "wants them". Once that's done we can try to test for broken stuff. If none of the plugins are broken then we can look at other possibilities. In fact, what's in this file?

```
gksudo gedit /etc/firefox/firefoxrc
```

---

### Post by XeroCurve on 2006-07-26
Just wanted to let you know I got things working but not with midi I am afraid. I reinstalled Breezy, ran EasyUbuntu then tweaked my web pages to function with WAVs instead and now I got everything to work like its supposed to. This is kind of a let down because I like using the latest versions of Ubuntu. I think the web pages might work on Dapper also but for now im leaving the office boxes with Breezy, because I got it all to work. The upside is that all of my office workers will be able to use Ubuntu boxes now that ive got it worked out, and hopefully the boss will see the value of Linux. My job is to make our website cross OS and cross Browser compatible and now that it works on both platforms it will be easier for all the people that use Linux to use our website now. I really apreciate all the help and suggestions. Im gonna stick with Breezy for now, but im sure we'll get this worked out or maybe not. I personally dont care if Firefox is ever midi compatible.

Sincerly Wits End

---

### Post by Peturrr on 2006-08-04
I got midi to work in firefox!!

You'll need to install timidity and mozplugger, mplayer can't play midi. The mozplugger gives a control interface for timidity on the webpage, so you can play/pause/stop.
```
sudo apt-get install timidity mozplugger
``` 
When you restart firefox it will now play embedded midi files. I will post a howto on the HowTO forum so other people will also know this.

---

