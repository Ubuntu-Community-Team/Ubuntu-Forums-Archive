---
title: "Mail notification in Thunderbird"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by DCMir on 2006-08-16
I'm having problems with mozilla Thunderbird mail notification in Kubuntu 6.06. Neither sound or alert work (nothing happens).

Someone?

---

### Post by Drakkor on 2006-08-16
Yeah, don't know much,but I selected a custom .wav file for notification and it plays when I open TB and have new mail and  . Guess there's no notification if you don't open TB.

---

### Post by DCMir on 2006-08-17
I tried already to use a custom wav and got no response. It is strange because the sound in Linux is working perfectly.

---

### Post by davebgimp on 2006-10-16
> **DCMir said:**
> I tried already to use a custom wav and got no response. It is strange because the sound in Linux is working perfectly.

I have the same issue. Sound is fine otherwise, but TB is silent.I tried using a custom .wav, but still no luck.

I wonder if this is the issue...
[http://www.ubuntuforums.org/showthread.php?t=169738&highlight=thunderbird+sound](http://www.ubuntuforums.org/showthread.php?t=169738&highlight=thunderbird+sound)

---

### Post by Drakkor on 2006-10-16
I'm using Dapper 6.06.1 with standard Ubuntu and Thunderbird mail, and I don't get a visual alert,but do get a custom .wav alert when new mail arrives. I do however leave Thunderbird open on desktop 4. What happens when you try to preview the custom .wav file ?

---

### Post by davebgimp on 2006-10-16
> **Drakkor said:**
> I'm using Dapper 6.06.1 with standard Ubuntu and Thunderbird mail, and I don't get a visual alert,but do get a custom .wav alert when new mail arrives. I do however leave Thunderbird open on desktop 4. What happens when you try to preview the custom .wav file ?

Zero sound - nothing.

---

### Post by wpshooter on 2006-10-16
> **DCMir said:**
> I'm having problems with mozilla Thunderbird mail notification in Kubuntu 6.06. Neither sound or alert work (nothing happens).

Someone?

What filesystem type are you using on your partitions ?

Seems to me that I had some sound problems on one of my applications a while back and strangely enough when I switched from ext2 to ext3, the problem went away.  Can not guarantee that this is what fixed it but I believe that it is.  Might want to give it a try when you get the opportunity.

Good luck.  I know that type of thing is really frustrating.

---

### Post by Kateikyoushi on 2006-10-16
On gentoo I do not have sound in Thundebird, I forgot what was the reason, probably a dependency issue but that install has less than 200 packages.

---

### Post by Drakkor on 2006-10-16
Hmmn..... don't know about that,but since I get a sound alert with Ubuntu/Gnome.......maybe a Kubuntu or KDE issue ??

---

### Post by Xappe on 2006-10-17
I use the app "mail notification" available in the reposistories. It supports both imap and pop mailboxes and shows popups on the desktop when new mail arrives. I think you could set it to play sounds too, if you activate the option to run a command (alsaplay <filename> perhaps?) when new mail arrives...

---

### Post by davebgimp on 2006-10-17
> **Xappe said:**
> I use the app "mail notification" available in the reposistories. It supports both imap and pop mailboxes and shows popups on the desktop when new mail arrives. I think you could set it to play sounds too, if you activate the option to run a command (alsaplay <filename> perhaps?) when new mail arrives...

Yeah, I use that as well. I'll give alsaplay a try.

---

### Post by kpprem@gmail.com on 2006-10-18
[http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/)

Try this extension for thunderbird. Its works perfectly and shows an icon in the system tray. I am using it for the last 3 months.

Thanks,
Prem

---

### Post by davebgimp on 2006-10-18
> **kpprem@gmail.com said:**
> [http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/)

Try this extension for thunderbird. Its works perfectly and shows an icon in the system tray. I am using it for the last 3 months.

Thanks,
Prem

The issue is with sound in Thunderbird, which that extension has nothing to do with.

---

### Post by DCMir on 2006-10-25
> **wpshooter said:**
> What filesystem type are you using on your partitions ?

Seems to me that I had some sound problems on one of my applications a while back and strangely enough when I switched from ext2 to ext3, the problem went away.  Can not guarantee that this is what fixed it but I believe that it is.  Might want to give it a try when you get the opportunity.

Good luck.  I know that type of thing is really frustrating.


I don't think it is about partitions or filesystem. Anyway I'm using ext3...

Now I'm also using Debian (Etch - testing version) in my computer and in this OS the problem with thunderbird does not occur.

---

### Post by esaym on 2006-11-02
Anyone have a wav of the sound that thunderbird is supposed to play?

---

### Post by Drakkor on 2006-11-03
Not for me,the default "system mail sound" never worked for me in either Dapper or now Edgy,as stated before,the custom wav sound works,and I keep 
TB open on my #4 desktop,works for me....  :)

---

### Post by lodp on 2006-11-06
I've got the same problem as some of the people above -- Thunderbird doesn't play any sounds, neither the system mail sound nor the custom one (i tried some .ogg file) works. I'm using Kubuntu, but as far as I remember it was the same in Gnome on Dapper.

---

### Post by Drakkor on 2006-11-06
I use a .wav file notification in Ubuntu/Gnome that works, it's a Simpson's
.wav of Nelson saying,"Haha",lol :p

---

### Post by lodp on 2006-11-07
just tried -- wav files don't work either...

---

### Post by Kateikyoushi on 2006-11-07
Custom wavs work in edgy but the system sound does not.

---

### Post by Nuafite on 2007-02-05
I've benefited so much from these forums since I started Ubuntu in the New Year that I hope I can contribute something back. I've had the same problem in Thunderbird - no sound, no pop-up notice.  I used Thunderbird in XP and tonight I remembered I had an extension called Mail Alert, and lo and behold, it works. Sound and pop-up notice are working. 
You can get the Mailbox Alert extension for Thunderbird 1.0-1.5.0 at
[https://addons.mozilla.org/thunderbird/2610/](https://addons.mozilla.org/thunderbird/2610/)

I can't guarantee that it won't interfere with other programs, but  it's solved this problem for me.

---

### Post by ember on 2007-04-25
I can also recommend Mailbox Alert. The latest version (0.12) works great in both Windows and Linux and now finally I have some nice notifications even in Ubuntu. That was something that really bothered me since I started using Linux every day.

---

