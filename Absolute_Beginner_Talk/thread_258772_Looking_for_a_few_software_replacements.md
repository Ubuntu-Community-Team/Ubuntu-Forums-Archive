---
title: "Looking for a few software replacements"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by liquilife on 2006-09-16
I'm completely new to Ubuntu here. I had some issues yesterday getting everything set up but it seems to be working like a champ now. I've got dual boot set up with WinXP and Ubuntu and am running the KDE desktop environment at the moment. I have to admit I'm becoming quite addicted, that being said...

I work from home doing web design full time. I am looking to replace some much needed software that could be used in Ubuntu. Here is a list of my software that I am looking to replace. Any reccommendations would be so very helpful :)

[LIST]
[*]Macromedia Suite (Dreamweaver, Fireworks, Flash)
[*]CuteFTP Pro
[*]TopStyle CSS Editor
[*]TigerColor (web and print color cooridinating program)
[*]Winamp (XMMS seems nice, any other nice alternatives?)
[*]MSN (I really need my Microsoft LifeCam VX-3000 to work for video conferencing as well for MSN)
[*]Internet Explorer 6.5 (I need this for website testing)
[*]Flash (I know the last version for *nix is 7, does this mean it's impossible to use v.9 with ubuntu through any other method?
[/LIST]
Well, I think that's about it for absolute essentials that need to be replaced. I installed WINE but I believe that works only when I install a windows program? Can I run my existing installs from my windows partition under WINE?

Thank you so much.

---

### Post by Marsolin on 2006-09-16
There are a lot of good apps you can check out. For web design I use [Quanta]("http://linuxappfinder.com/package/quanta"). It integrates well with KDE, has CSS editing, and FTP support.

Flash is a little trickier, but options are improving. [F4L]("http://linuxappfinder.com/package/f4l"), [OpenLaszlo]("http://linuxappfinder.com/package/openlaszlo"), and [Uira]("http://linuxappfinder.com/package/uira") are a few you can start with.

For general FTP programs you can use [Konqueror]("http://linuxappfinder.com/package/konqueror") (through the ftp:/ kio_slave), [Kasablanca]("http://linuxappfinder.com/package/kasablanca"), or [KFTPGrabber]("http://linuxappfinder.com/package/kftpgrabber").

[amaroK]("http://linuxappfinder.com/package/amarok") and [Beep]("http://linuxappfinder.com/package/beep-media-player") are two audio players I'd check out. I use amaroK, but Beep supports WinAmp skins.

[Kopete]("http://linuxappfinder.com/package/kopete"), [Gaim]("http://linuxappfinder.com/package/gaim"), [aMSN]("http://linuxappfinder.com/package/amsn"), and [KMess]("http://linuxappfinder.com/package/kmess") are among the MSN compatible instant messengers.

For Internet Explorer and Flash 9, the best method is using [Wine]("http://linuxappfinder.com/package/wine") or running Windows in [VMware Player]("http://linuxappfinder.com/package/vmwareplayer"). Flash player 9 is being worked on for Linux, but it isn't ready yet.

Hopefully those can help you out.

---

### Post by liquilife on 2006-09-16
Thank you Marsolin, I am a bit confused with Wine. I've installed it but I can't seem to run any applications under it. I'm sure it's just my own ignorance being I am so new at this but... would I need to re-install my windows apps under wine or can I run them from my WinXP partition using Wine?

I actually found quite an extensive list for alternate programs at [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) :) Between your suggestions and that list I guess I'll be busy for a while.

---

### Post by Marsolin on 2006-09-16
I believe you would need to reinstall the Windows apps under Wine. That's the only way I have ever done it.

---

### Post by shiellb on 2006-12-25
I'm relatively new to Ubuntu and I need to work with Solidworks.  If I use Wine, can I use Solidworks or should I use something else?

---

### Post by Regel on 2006-12-25
> Flash (I know the last version for *nix is 7, does this mean it's impossible to use v.9 with ubuntu through any other method?
Actually, there's this flashplayer-nonfree version 9 package in the repository. You can install it and use it with ubuntu.

---

### Post by macogw on 2006-12-25
Google for IE4Linux to get IE 5, 5.5, and 6.  Yes, with Linux, you can install all 3 simultaneously, while Windows will only take one at a time.

Gaim does MSN chatting.  Check and see if your webcam is supported.  Mine isn't V4L (Video for Linux) supported, but the driver happens to be in the kernel anyway, so it works fine.

I can't say much about web design.  I don't believe in using Flash.  It's terrible for accessibility since the text is turned into pictures and therefore can't be read by screenreaders.  I consider that a poor plan.  Target was sued (and lost) for poor accessibility on their website.  I have pretty much always done my web design in MS Notepad, and now I use either gedit or vi.

---

### Post by mexlinux on 2006-12-25
it's ies4linux

---

### Post by macogw on 2006-12-25
Eh it shows up on Google with either one.  I think the website is tatanka.com or somethin

---

### Post by rabideau on 2007-04-08
Topstyle runs fine under Wine....:KS :KS

---

