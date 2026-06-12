---
title: "Final solution on java please"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by UpSignal on 2008-04-02
Hello my friends. Believe me, i'm posting this as my last chance:

Everybody knows that if you run an java applet on firefox, it plays sound good...but you can't listen any sound on the rest of the computer, because java makes the device busy. now, i've tried to change the firefox sound by following this:

> 1. Goto a terminal and type 'sudo gedit /etc/firefox/firefoxrc' .
2. On the file that it opens look for the line FIREFOX_DSP=
3. If after the equals sign it says 'none' or anything else except 'aoss' then carry on with these instructions. If it already says 'aoss' then your problem isn't the same as mine.
4. Close the text editor, without making any modifications yet.
5. Go back to the terminal and type 'sudo apt-get install alsa-oss' .
6. Once it has installed write 'sudo gedit /etc/firefox/firefoxrc' again.
7. Find the line 'FIREFOX_DSP=' and change it to FIREFOX_DSP='aoss' (keep the commas around the aoss bit).
8. Save the file and exit the text editor.
9. Close any firefoxes that you have open.

I've done it a million times. problem remains.
The issue is really about java, because i can hear videos on youtube and play music on amarok or Xine at the same time. As soon as i launch an java applet it just sucks all the sound! 
There must be a way to solve this, i know it must :) help!

---

### Post by doorknob60 on 2008-04-02
For me, starting Firefox with aoss works fine, without any other changes. Just change your launcher to "aoss firefox" wihtout the quotes. First, make sure you have aoss installed though, or itwon't work. It might also make the other way work.
```
sudo apt-get install alsa-oss
```

---

### Post by UpSignal on 2008-04-02
Thanks for the fast reply. But didn't work :(
It's funny...the sound only comes back, as soon as i close firefox. then i can listen my mp3 or Msn sounds. There must be a way to change the java sound engine or something. or even....is there any other java solution, besides javasun?

---

### Post by UpSignal on 2008-04-03
bump

---

### Post by UpSignal on 2008-04-05
omg, no one can help me? :s

---

### Post by SunnyRabbiera on 2008-04-05
I dont think there is a way to fix this yet...

---

### Post by UpSignal on 2008-04-06
thanks for the reply. do you think hardy will fix it? or it's just a java problem?

---

### Post by jhnphm on 2008-04-10
Figured it out!

Move or remove /usr/lib/jvm/java-6-sun/jre/lib/amd64/libjsoundalsa.so (for AMD64) or /usr/lib/jvm/java-6-sun/jre/lib/i386/libjsoundalsa.so (for 32 bit) and run Firefox, or anything that calls or runs Java w/ "padsp [appname]" (for Hardy), or install the alsa-oss package and use "aoss [appname]" (for Gutsy and below)

Modify .desktop files appropriately

---

### Post by UpSignal on 2008-04-10
> **jhnphm said:**
> Figured it out!

Move or remove /usr/lib/jvm/java-6-sun/jre/lib/amd64/libjsoundalsa.so (for AMD64) or /usr/lib/jvm/java-6-sun/jre/lib/i386/libjsoundalsa.so (for 32 bit) and run Firefox, or anything that calls or runs Java w/ "padsp [appname]" (for Hardy), or install the alsa-oss package and use "aoss [appname]" (for Gutsy and below)

Modify .desktop files appropriately

Heyyyyy, awesome dude! But, i don't understand. i deleted that file, now what? java doesn't have sound right now. i already have alsa installed
what do you mean with: use "aoss [appname]"

I did this:

sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=&#8221;aoss&#8221;

But it's still not working. no sound on java, since i deleted that file. any tips?

---

### Post by jhnphm on 2008-04-10
That should do it.... do you have the alsa**-oss** package installed? 

As for "aoss appname", I meant if you wanted to launch firefox, you would type "aoss firefox" into the command line.

---

### Post by taavikko on 2008-04-10
The best bet is to change other players to use other audio output-modules.
I've never had any problems with sound on youtube via firefox, even other  sources of sound coming out; movie playing and music playing all the same time.

Edit: Just tested, testing java virtual machine on one tab
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
and audacious playing.
and other tab youtube open 

All worked, sound, java, flash+sound

---

### Post by UpSignal on 2008-04-10
> **taavikko said:**
> The best bet is to change other players to use other audio output-modules.
I've never had any problems with sound on youtube via firefox, even other  sources of sound coming out; movie playing and music playing all the same time.

Edit: Just tested, testing java virtual machine on one tab
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
and audacious playing.
and other tab youtube open 

All worked, sound, java, flash+sound

Well, i would have to change all my players, incluiding IM programas, IRC programs... and all the stuff. not a very good idea. Java is the one causing me troubles. I launched with:
"aoss firefox"
and the java still doesn't have sound. i don't know what to do anymore :s
i have the alsa package installed

---

### Post by igknighted on 2008-04-10
Pulse Audio in Hardy should fix this.  Try the beta or check out Fedora 8 or Mandriva 2008.1 if you want to test via a stable version.

---

### Post by UpSignal on 2008-04-10
hum, 14 days to the official release. hardy should be pretty stable by now, huh? with the updates and such. would you recommend me to install?

---

### Post by jhnphm on 2008-04-10
I'd just upgrade to Hardy if you don't mind downloading a large number of packages. Still needs the remove libjsoundalsa fix though for my 32 bit chroot. 
And alsa != alsa-oss package,

When upgraded to Hardy w/ pulseaudio, use padsp instead of aoss. You could try just installing pulseaudio on gutsy, but it might break things (you'll have to configure all your other apps to use pulse by default, and/or change the default alsa device to route to pulseaudio).

---

### Post by jhnphm on 2008-04-11
Now that I've retested aoss, it doesn't seem to really work at all (didn't test too much since using Hardy where pulse is the default)- padsp works  (reliably) though.

---

### Post by UpSignal on 2008-04-11
Complete disaster. i've upgraded to hardy, done all the updates and:
Apart from the audio got all messed up, my USB mouse keeps disconnecting from time to time.
I open a video on youtube, it's ok...sound ON. i open a music on amarok at the same time...says no audio device. So, let's make a summary:

Gutsy -> Audio working at the same time with all aplications except Java
Hardy -> Audio working on 1 application at time

I think i can live without java. Anyway, i'm gonna format and install hardy from the scratch. just to make sure it wasn't a problem with the upgrade. If hardy goes this way again, i'm going back to gutsy and forget that runescape exists (java game online)

Thanks for all the replies guys

---

### Post by jhnphm on 2008-04-11
You probably oculd have just done asoundconf set-pulseaudio to enable all apps that use alsa to use pulseaudio. Amarok probably also has a pulseaudio backend. You also have to install libflashsupport I believe- is flash from the package or manually installed?

---

### Post by UpSignal on 2008-04-20
i just installed hardy again. I'm gonna put all steps here:

[LIST]
[*]Installed all updates
[*]installed Envy Nvidia driver
[*]installed flash player to open youtube videos
[*]installed amarok player
[*]installed Emesene (with sound plugin)
[/LIST]

Ok, so, i open a video on youtube, it starts playing good and with sound enabled. so, i open emesene and chat with someone....and no sound. just youtube playing..
I close firefox and emesene, then turn emesene on again, and i have sound.

Please, someone help me! i tried the command 
> asoundconf set-pulseaudio

And rebooted. but is stays the same! i cannot play sound from more than 1 application at time. this is so annoying

---

### Post by UpSignal on 2008-04-20
bump!
come on guys, help me out. i went to IRC and nobody couldn'te help me either. That's weird, i can't believe i'm the only one having this issues. Hardy comes with pulse, right? so if i install alsa package, will it fix?

---

### Post by UpSignal on 2008-04-20
bump

---

### Post by UpSignal on 2008-04-21
ok, last bump. I see no experts can help me

---

### Post by jhnphm on 2008-04-21
Um, email notification for a lot of people is only sent once every 24 hours

Anyway...

Has gnome sound preferences been set to use pulseaudio? CHeck under system->preferences->sound

---

### Post by jhnphm on 2008-04-21
And what is this "alsa package"? What's the full name of that package- AFAIK, there's no package named just "alsa" 


Plus, not too many people use emesene, AFAIK, most use Pidgin or AMSN


Also, did you install flash manually or via package, since the package also pulls down libflashsupport which is required for proper pulseaudio w/ flash.

---

### Post by UpSignal on 2008-04-21
I checked them now. i set all of them to pulse audio. but it stays the same :S

---

### Post by UpSignal on 2008-04-21
i installed flash via firefox (clicked install missing plugins)

---

### Post by UpSignal on 2008-04-21
Holy christ!!! i installed that libsupport, and now it works!! I LOVE YOU MAN, wooooooooooooo!!!!!!!!!11

---

