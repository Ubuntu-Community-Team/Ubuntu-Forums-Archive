---
title: "Does Skype work in Ubuntu?"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-08-03
Hi
Today I installed Skype 1.3 (for Debian) 
Note that I have used Skype 2.0 for Windows for quite some time without any problems.

However, in Ubuntu 6.06, Skype seems extraordinarily temperamental.
The first time I opened it, my contacts box opened without difficulty (although very slowly) and I was able to make one call.

However, ALL subsequent attempts to use Skype in Linux have resulted in either a failure to recognize my password and username or (if the contacts box actually opened) in a "call failure" error.
Anybody got a workaround?

Thanks
Paul

---

### Post by ironfistchamp on 2006-08-03
1.3 is the beta isn't it? have you tried the 1.2 stable from there site. Could just be a problem with the beta.

I've just seen a Skype alternative called openwengo

[http://dev.openwengo.com/trac/openwengo/trac.cgi/wiki/WengoPhoneNG](http://dev.openwengo.com/trac/openwengo/trac.cgi/wiki/WengoPhoneNG)

That might be something to look at.

---

### Post by BobSongs on 2006-08-03
Is OpenWengo compatible with Skype? Or does it work on an entirely different protocol?

---

### Post by ironfistchamp on 2006-08-03
That I can't answer as I use neither of them. Sorry.

---

### Post by BobSongs on 2006-08-03
I'm asking because I'm using Skype right now. I can hear myself in the headphones. Sound is indeed entering into the microphone and the mike boost is active. However, recipients on the other end don't hear me. I'm not sure why. I've just begun to investigate.

---

### Post by PaulFXH on 2006-08-03
Interesting replies.
Both here and in other posts I've seen on this topic, there seem to be many problems trying Skype in Ubuntu.
However, I'd love to know does Skype actually work for ANYBODY in this OS meaning that the problems are isolated and , therefore curable.

Incidentally, I made an error in my OP. I had actually installed ver.1.2 earlier with which I had issues (although it DID work once).
So, now I've installed the beta which displays similar sporadically problematic behaviour.

So, if anybody is successfully using Skype from Ubuntu, please let us know how you did it.

Thanks
Paul

---

### Post by mjpatey on 2006-08-03
I'm able to use the text chat function just fine, and can hear people on the other end, but they can't hear me.

---

### Post by PaulFXH on 2006-08-03
Hi mjpatey
Sounds like you have a problem with your microphone.
Does it work when you try to record your voice or use it in the Skype test?

Nevertheless, although your experience sounds promising, I would like to hear from ANYBODY who positively has Skype working reliably on a Ubuntu OS......

...................or alternatively, ANY telephony app with similar functions to Skype.

Thanks
Paul

---

### Post by atenlaugh on 2006-08-03
Skype works fine for me. Not sure what else to say!

---

### Post by NT4usB on 2006-08-03
I've installed it and configured it but haven't actually talked to anyone yet (I have a grand total of one contact I use it for.)
I'll call her tonight and report back!

---

### Post by cantormath on 2006-08-03
> **PaulFXH said:**
> Hi
Today I installed Skype 1.3 (for Debian) 
Note that I have used Skype 2.0 for Windows for quite some time without any problems.

However, in Ubuntu 6.06, Skype seems extraordinarily temperamental.
The first time I opened it, my contacts box opened without difficulty (although very slowly) and I was able to make one call.

However, ALL subsequent attempts to use Skype in Linux have resulted in either a failure to recognize my password and username or (if the contacts box actually opened) in a "call failure" error.
Anybody got a workaround?

Thanks
Paul

The easiest way to install skype, is with automatix.
Here are the directions:
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

Just install it, and click on skype, and thats it.
make sure when you are done, to click yes when it asks to restore your repositories.

---

### Post by PaulFXH on 2006-08-04
Hi to everybody and thanks for the replies.

From atenlaugh's comments, it appears that Skype CAN work successfully in Ubuntu. However, it would be interesting to hear from atenlaugh what version of Skype he/she is using, has there ever been any problems at all and, finally, how intensively it is used.

I'm using Skype 1.3 Beta since yesterday with Dapper. After boot up I can use Skype without problems (other than the cost of the calls :D )
However, once the app is shut down, if I try again, I get an error message:

> Skype has experienced a database error. Make sure your profile files in ~/.Skype are intact and have proper permissions and then restart Skype.

Rebooting gets things working again, but only until the next time I shutdown Skype.

Sound familiar to anybody?

Paul

---

### Post by Obor on 2006-08-04
> **BobSongs said:**
> Is OpenWengo compatible with Skype? Or does it work on an entirely different protocol?

As far as I know you can't call skype users with OpenWengo. I'm using both (openwengo instead of Gaim as it also supports IM - MSN, Yahoo, ICQ etc.)

Skype works on my laptop since the 1.3 Beta (supports ALSA) although my mic doesn't work as good as in Win (not skype problem) and the sound quality is not as good either IMHO.

---

### Post by whiteB on 2006-08-04
He..
 I also faced some problems when I upgraded skype 1.3 beta .deb package.
 I converted Skype1.3 beta RPM package to .deb and installed and now working
 fine with UBUNTU6.06 ...

---

### Post by Dinerty on 2006-08-04
I just added:

## skype (official)
## only uncomment it if you need it
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

to my sources.list

then installed from terminal, works fine here

---

### Post by Ambimom on 2006-08-04
I have used Skype successfully in Ubuntu, however it only works PC to PC.  My contacts were visible when I signed in to my regular account.    

As for hearing yourself in the microphone....actually your microphone should be muted.  You can set up the audio in the same way you do in the Windows version.  My sound quality was excellent and the connection very clear.

Skypeout and Video do not work in the Linux version.

---

### Post by PaulFXH on 2006-08-04
Thanks for all of the replies and comments.
However, I should have been more specific in my grumbling. My problems with Skype in Ubuntu refer EXCLUSIVELY to SkypeOut which Ambimom says doesn't work in Linux.

Actually, I have got it to work, but only immediately after rebooting. Once Skype is shut down, it won't enable SkypeOut calls until after I reboot again.

For those that said Skype works fine for them, were you referring to PC-to-PC calls or to PC-to Phone?

Thanks 
Paul

---

### Post by Dinerty on 2006-08-04
> **PaulFXH said:**
> Thanks for all of the replies and comments.
However, I should have been more specific in my grumbling. My problems with Skype in Ubuntu refer EXCLUSIVELY to SkypeOut which Ambimom says doesn't work in Linux.

Actually, I have got it to work, but only immediately after rebooting. Once Skype is shut down, it won't enable SkypeOut calls until after I reboot again.

For those that said Skype works fine for them, were you referring to PC-to-PC calls or to PC-to Phone?

Thanks 
Paul

PC to PC calls here :)

---

### Post by PaulFXH on 2006-08-04
I've just come across this link to Skype problems in Ubuntu which seems to imply that at present it's never going to work quite as well as it does in Windows.

> [https://help.ubuntu.com/community/Skype?action=show&redirect=SkypeHowto](https://help.ubuntu.com/community/Skype?action=show&redirect=SkypeHowto)

I haven't tried the workarounds suggested yet but they're on my agenda.

BTW, is anybody using anything else that does reliably allow PC-to-Phone calls from Linux?

Thanks
Paul

---

### Post by Dr. Cox on 2006-08-12
a much bigger problem, i think, is the lacking video support of the linux version of skype... or can anyone see anyhting if his counterpart uses a webcam?

is there a program that can communicate with skype and make use of the video option?

---

### Post by mich_r on 2006-08-12
I am using skype on Dapper , it performs OK.
I remember that I had problems with debian skype package, so I converted fedora package (with alien) to get it running. I've heard the fixed version is also available somewhere in the ubuntu wiki.

I had problems with "hanging dsp" bug, but I get rid of it with "skype dsp hijacker" , just google for it.

---

### Post by PaulFXH on 2006-08-12
Hi
Thanks for your reply.
I really thought that your suggestion to use the Fedora package was going to remove the persistent difficulties i have with Skype 1.3 in Ubuntu.
So, I removed what I had and installed the Fedora 1.2 version.
Unfortunately, it is no better and, actually worse on my machine than what I already had.

Although i can make calls, it's still one at a time and then I must reboot to  get Skype functioning again (this is the same as I get with 1.3).
However, with the Fedora version, Skype needs quite some persuasion before recognizing my Skype name. In general, it opens without my contact list. When I try to sign in, I get a "login failure" message.
The only way around this is for me to shutdown Ubuntu and boot back into WinXP, open up my account page in Skype and then go back into Ubuntu.

Perhaps you have some comments on something i might have overlooked?

BTW, what is the "alien" you mentioned?

Thanks
Paul

---

