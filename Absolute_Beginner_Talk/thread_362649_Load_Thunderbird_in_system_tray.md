---
title: "Load Thunderbird in system tray"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by jordon on 2007-02-15
I want to have Thunderbird running minimized in the system tray when I log in. I downloaded AllTray for this purpose, but I can't get it to automatically start Thunderbird at startup, even after following the directions from the [FAQ]("http://alltray.sourceforge.net/faq.html").

Now I have two problems:

1. I don't know how to uninstall AllTray. (I installed it from a .package file.)
2. I can't get Thunderbird to load minimized in the tray.

Can anyone help?

---

### Post by kolinab on 2007-02-15
I think you might be able to uninstall AllTray through Synaptic. Even though you didn't install it with Synaptic I think I learned somewhere that it keeps track anyway. Search for it in synaptic and you should be in luck. 

I minimise Thunderbird to the tray with an extension called 'New Mail Icon.'

[http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/)

At first I didn't see how it minimised T-bird to the tray, but you have to right click the icon and select 'hide window.'

I love this little extension. I used to keep T-bird open on another workspace, but now I just minimise it to the tray.

Let me know if you have any problems getting this working.

K

---

### Post by dpar on 2007-02-15
You can get a Minimizetotray extension for Thunderbird. Have you tried that??

---

### Post by chaplanger on 2007-02-15
> **jordon said:**
> I want to have Thunderbird running minimized in the system tray when I log in. 

Jordan,
When you say "system tray" are you referring to the panel at the top of the page?  If so simply go to Applications>Internet> and right click on the Thunderbird icon.  Select "Add this launcher to panel" and I believe you will have what you are looking for.

---

### Post by jordon on 2007-02-16
Thanks! That's pretty much what I wanted. I was hoping that I could get Thunderbird to start minimized in the tray upon logging in, but I'll start it manually and then minimize it. That's what I had to do in Windows, anyway.

---

### Post by kolinab on 2007-02-16
I'm sure there's a way to load Thunderbird automagically at startup. I haven't looked in to it though. Someone here can tell you I'm sure.

Cheers to moztrraybiff.

---

### Post by jordon on 2007-02-17
There is a way, and I actually did it by going to System -> Preferences -> Sessions -> Startup Programs, and adding "mozilla-thunderbird." But it starts maximized, which is kind of unsettling to me when I log in.

---

### Post by kobewan on 2007-03-15
Try this instead ```
alltray mozilla-thunderbird
```

---

### Post by hod139 on 2007-03-15
An alternative is mail-notification.  It is a small gnome applet that does exactly what you want.

---

### Post by pohlipit on 2007-04-22
So is there no way to minimise it to the tray in the same way Outlook does that in Windows? I mean when you click on the minimise window icon in Thunderbird for it to be removed from the task bar and only be visible in the tray. Similar to GAIM.

Cheers,
 Pete

--------------
Guys,
forget about this message. Just found the minimise to tray extension and it does exactly what I was looking for

---

### Post by olavjunior on 2007-04-23
So, does the "New Mail Icon" work for thunderbird2?

And to place a shortcut for thunderbird in the dock, isn't what I'm looking for. 
I want the same as outlook in windows, that it stays hidden while checking for new mail, and notefying me about it. 

I didin't understand the new-mail notefyer from synaptics. Isn't there any easy way?
I really doesn't understand why this isn't implemented in thunderbird....

---

### Post by hod139 on 2007-04-25
The package mail-notification does exactly what you want.  It is a separate application from the mail reader.  It is an applet that checks for new mail and gives pop up notifications when new mail arrives.  You can specify a preferred reader, so the applet can open your reader as well.

---

### Post by kolinab on 2007-04-25
There now exists a workaround if you wish to use the minimise to tray extension.

See info at [http://ubuntuforums.org/showthread.php?t=414714](http://ubuntuforums.org/showthread.php?t=414714)

[edit] This valiant workaround seems to mostly work for me. The new mail notification doesn't seem to work.

---

### Post by gmc on 2007-04-27
> **kolinab said:**
> I think you might be able to uninstall AllTray through Synaptic. Even though you didn't install it with Synaptic I think I learned somewhere that it keeps track anyway. Search for it in synaptic and you should be in luck. 

I minimise Thunderbird to the tray with an extension called 'New Mail Icon.'

[http://moztraybiff.mozdev.org/](http://moztraybiff.mozdev.org/)

At first I didn't see how it minimised T-bird to the tray, but you have to right click the icon and select 'hide window.'

I love this little extension. I used to keep T-bird open on another workspace, but now I just minimise it to the tray.

Let me know if you have any problems getting this working.

K

Thanks for the pointer. Just so anyone trying to use this plugin with Thunderbird2. You'll have to edit the "install.rdf" file and change the value of maxVersion to "2.0+" (maxVersion is about 10 lines from the top).

Regards
Gord

---

### Post by RikoW on 2007-04-27
Hi,

actually missing the notification extension was one of the big drawback in switching to thunderbird2.

> **gmc said:**
> Thanks for the pointer. Just so anyone trying to use this plugin with Thunderbird2. You'll have to edit the "install.rdf" file and change the value of maxVersion to "2.0+" (maxVersion is about 10 lines from the top).

Regards
Gord

It installed fine, but doesn't seem to work - never get any notification :(  this is what I did:

```

> unzip mozTrayBiff-1.2.2-tb1.5.xpi
Archive:  mozTrayBiff-1.2.2-tb1.5.xpi
   creating: platform/
   creating: platform/Linux_x86-gcc3/
   creating: platform/Linux_x86-gcc3/components/
  inflating: platform/Linux_x86-gcc3/components/libtraybiff.so
  inflating: components/libtraybiff.xpt
  inflating: chrome/tray-biff.jar
  inflating: defaults/preferences/tray-biff.js
  inflating: install.rdf
> emacs install.rdf    # change version as described above
> zip -r mozbiff-1.2.2.xpi chrome components defaults install.rdf platform
  adding: chrome/ (stored 0%)
  adding: chrome/tray-biff.jar (deflated 39%)
  adding: components/ (stored 0%)
  adding: components/libtraybiff.xpt (deflated 31%)
  adding: defaults/ (stored 0%)
  adding: defaults/preferences/ (stored 0%)
  adding: defaults/preferences/tray-biff.js (deflated 45%)
  adding: install.rdf (deflated 61%)
  adding: platform/ (stored 0%)
  adding: platform/Linux_x86-gcc3/ (stored 0%)
  adding: platform/Linux_x86-gcc3/components/ (stored 0%)
  adding: platform/Linux_x86-gcc3/components/libtraybiff.so (deflated 58%)

```


anything I'm missing?

Cheers,

                Riko

---

### Post by gmc on 2007-04-27
> **RikoW said:**
> Hi,

actually missing the notification extension was one of the big drawback in switching to thunderbird2.



It installed fine, but doesn't seem to work - never get any notification :(  this is what I did:

```

> unzip mozTrayBiff-1.2.2-tb1.5.xpi
Archive:  mozTrayBiff-1.2.2-tb1.5.xpi
   creating: platform/
   creating: platform/Linux_x86-gcc3/
   creating: platform/Linux_x86-gcc3/components/
  inflating: platform/Linux_x86-gcc3/components/libtraybiff.so
  inflating: components/libtraybiff.xpt
  inflating: chrome/tray-biff.jar
  inflating: defaults/preferences/tray-biff.js
  inflating: install.rdf
> emacs install.rdf    # change version as described above
> zip -r mozbiff-1.2.2.xpi chrome components defaults install.rdf platform
  adding: chrome/ (stored 0%)
  adding: chrome/tray-biff.jar (deflated 39%)
  adding: components/ (stored 0%)
  adding: components/libtraybiff.xpt (deflated 31%)
  adding: defaults/ (stored 0%)
  adding: defaults/preferences/ (stored 0%)
  adding: defaults/preferences/tray-biff.js (deflated 45%)
  adding: install.rdf (deflated 61%)
  adding: platform/ (stored 0%)
  adding: platform/Linux_x86-gcc3/ (stored 0%)
  adding: platform/Linux_x86-gcc3/components/ (stored 0%)
  adding: platform/Linux_x86-gcc3/components/libtraybiff.so (deflated 58%)

```
anything I'm missing?

Cheers,

                Riko

That works, but isn't it easier to just use the archive manager (gnome) to open the xpi file, drag the install.rdf file to the desktop, edit it and drag it back into the archive manager and then install ?

As for working, I don't know. It minimizes thunderbird to the taskbar just fine, though I'm not noticed it change icons when there's waiting mail.

Gord

---

### Post by RikoW on 2007-04-27
> **gmc said:**
> That works, but isn't it easier to just use the archive manager (gnome) to open the xpi file, drag the install.rdf file to the desktop, edit it and drag it back into the archive manager and then install ?

Gord

Probably! :) But I'm an 'old-timer' quite used to the command line, so often I don't realize there are GUI ways these days :)

Anyway, minimizing to tray indeed works, but I'm mostly missing the changing icon, when there is mail waiting. The new build-in notification with the pop-up doesn't do much good, if you are away from your desktop for a bit.
In fact, after installing mozbiff, this build-in notification doesn't pop up anymore, just the sound file plays ....

- Riko

---

### Post by Kent84 on 2007-04-30
No tray icon and no sound for me with (modified) Mozzbiff & Thunderbird 2. Any chance of someone who knows about writing Firefox extensions update Mozzbiff?

---

### Post by Billy McCann on 2007-04-30
I'm really interested in this too.  

From the website --

"(In development) -Turbo option for Firefox and Thunderbird.  MinimizeToTray implements this popular feature from the Mozilla application suite. Have a Firefox tray icon and menu always available, even if no browser window is open. ** Or have Thunderbird launch directly into the tray only to notify you if you receive mail.**"

Apparently this is still in development.  Shouldn't be too long, I don't guess.  

[http://minimizetotray.mozdev.org/](http://minimizetotray.mozdev.org/)

---

### Post by Kent84 on 2007-04-30
Just played around with the "Mail Notification" program that's in the repositories... works quite well but I prefer to have everything centralised to one program (i.e. thunderbird).

---

### Post by kolinab on 2007-05-01
> **Kent84 said:**
> Just played around with the "Mail Notification" program that's in the repositories... works quite well but I prefer to have everything centralised to one program (i.e. thunderbird).

I have tried the same and agree with what you say exactly. When the extension worked perfectly life was better. That should teach me for moving ahead to TB2 when I really didn't need it. I should have stayed with 1.5 until the extension is tweaked for TB2 etc. I guess I can always go back. For now, I stay tuned for updates!

K

---

