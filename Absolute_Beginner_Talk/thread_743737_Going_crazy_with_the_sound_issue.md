---
title: "Going crazy with the sound issue"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by YourHonor on 2008-04-02
I think I'm going to lose it....my son installed Ubuntu on my Toshiba laptop and I have no sound. If you can help I need you to speak in the most simple language possible as I am one of those people who should not have Ubuntu but the old standby stuff. So please go easy on  me. I also can't figure out how to run my Napster stuff. I used to do it in Windows Media.

---

### Post by Samurai Penguin on 2008-04-02
when I had no sound with my set up this is what I did. Might be similar for your
laptop. Where it says "select Audigy 1 [SB0090] (Alsa mixing)" you would of coarse
select your on-board sound device (AC 97 or whatever) or a sound card if one is
installed.

Volume Control > File > Change Device > select Audigy 1 [SB0090] (Alsa mixing)
Volume Control > Switches Tab > uncheck Audigy Analog/Digital Output Jack

---

### Post by Xiong Chiamiov on 2008-04-02
[This]("http://ubuntuforums.org/showthread.php?t=455147") is the guide I've used to get my sound working on a few computers (though I'm using the newest versions of the drivers that have come out since then).  Unfortunately, sound on Linux is not yet where it should be, due a lot to a wide variety of soundcard manufacturers.  As to why your son installed Ubuntu (and erased Windows) without helping you understand it, that's something you have to take up with him.  I'm a bonified geek and it took some effort to get things working for me.

---

### Post by BandD on 2008-04-03
YourHonor, let's try to get a little more info first.

Go to Applications-->Accessories-->Terminal

That will open up a window with the name of your computer on the first line which should look something like:

```
bandd@BandD-laptop:~$
```

And there will be a little blinking box.

Please cpoy the below text into this Terminal window:

```
lspci | grep Audio
```

(If you want to copy and paste, you can copy from your internet browser normally, and to paste the text in the Terminal press Ctrl+Shift+V)

Then hit enter.  It should spit out a line or two.  Please copy and paste that line back here.  (Again to Copy, highlight the text in the terminal and press Ctrl+Shift+C and paste it in your borwser as usual)

That will help us know how to help you better.

Thanks,

Dustin

---

### Post by Gazneth on 2008-04-03
Here is a link that should help you solve your problem. Sorry it's all command line work. Copy and paste the lines into the terminal one at a time. This is a common problem with Intel HDA audio. Good luck.[http://ubuntuforums.org/showthread.php?t=416207&highlight=toshiba+sound+howto]("http://ubuntuforums.org/showthread.php?t=416207&highlight=toshiba+sound+howto")

---

