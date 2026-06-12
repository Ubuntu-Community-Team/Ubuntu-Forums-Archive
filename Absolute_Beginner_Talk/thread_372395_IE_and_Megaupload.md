---
title: "IE and Megaupload"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Zero.The.Hero on 2007-02-28
Hi. I'm facing a problem here... I need to download some stuff from megaupload.com, and, as you all know, this shitty file hosting site requires IE. That wouldn't be a problem, since I successfully installed IEs4Linux, but moreover it says that there are no free upload slots for your location and then demands you to download their super dooper megaupload toolbar... Arrghh! How could I possibly make that work? I tried to run the installer with wine but it told me that I needed at least IE5 to proceed....

Did any of you manage to get downloads off megaupload.com possible under Ubuntu ? If so... please be kind and share your knowledge, I'm stunned at why people still use that crappy megaupload.com instead of other file hosting services... which *don't* require IE and Win.

---

### Post by xpod on 2007-02-28
Aint this any good for that kind of thing??

[https://addons.mozilla.org/firefox/59/](https://addons.mozilla.org/firefox/59/)

---

### Post by mhancoc7 on 2007-02-28
> **Zero.The.Hero said:**
> Hi. I'm facing a problem here... I need to download some stuff from megaupload.com, and, as you all know, this shitty file hosting site requires IE. That wouldn't be a problem, since I successfully installed IEs4Linux, but moreover it says that there are no free upload slots for your location and then demands you to download their super dooper megaupload toolbar... Arrghh! How could I possibly make that work? I tried to run the installer with wine but it told me that I needed at least IE5 to proceed....

Did any of you manage to get downloads off megaupload.com possible under Ubuntu ? If so... please be kind and share your knowledge, I'm stunned at why people still use that crappy megaupload.com instead of other file hosting services... which *don't* require IE and Win.

I have just tested this with the new IE .deb package that I have built. It installed fine. I have not tested to see if it works correctly.

1. Download and install the new IE deb package available here.
[http://www.ubuntulabs.devubuntu.com/deb](http://www.ubuntulabs.devubuntu.com/deb)
2. Install the deb package. Don't worry this will not affect your current wine configuration or any other IEs that you have installed to wine.
3. Run IE from the menu (Applications>Internet).
4. Once setup has completed download the megaload toolbar to "Desktop". This should be the default download location. This is not your real Desktop it is the IE deb package Desktop.
5. Close IE
6. Run the following in a Terminal. Replace YOURUSERNAME with your user name.
WINEPREFIX=/usr/local/apps/ie4linux/ie4linux wine ```
/usr/local/apps/ie4linux/ie4linux/dosdevices/c:/windows/profiles/YOURUSERNAME/Desktop/megauploadtoolbarsetup.exe
```
7. The Terminal will appear to get stuck after install finishes. Just close the Terminal.
8. Run IE and there is the toolbar.
9. Now test it and let me know if it worked! :)

Hope that helps, Jereme

---

### Post by Zero.The.Hero on 2007-02-28
Hi and thanks for your help :)

I doubt the Firefox addon for changing the user agent would be of any help, that crappy megaupload.com requires IE for the toolbar to be installed... and yes, if you don't have the toolbar, you can't download! This is dictatorship!!! 

Anyways... I tried what mhancoc7 suggested, thanks, I went OK from steps 1-5... The problem was that, when I tried to run 
```
/usr/local/apps/ie4linux/ie4linux/dosdevices/c:/windows/profiles/root/Desktop/megauploadtoolbarsetup.exe
```I got```
bash: /usr/local/apps/ie4linux/ie4linux/dosdevices/c:/windows/profiles/root/Desktop/megauploadtoolbarsetup.exe: cannot execute binary file
```
so I figured I'd need to try with wine, which I did and got the following (after many many lines):```
wine: '/root/.wine' created successfully.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
..............................................................................
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```
Err... and the next time I tried to run it, I got a window with the caption "Megaupload Toolbar 1.0 Setup", stating that "Aborting installation. You need to have Microsoft Internet Explorer version 5.0 or greater to continue. >> OK <<" Ughh...

I don't think anything went wrong, and the only thing I can think of is the fact that I ran the setup as root, but this was because when I first started IE I had to enter my root password (at the first run) and seems I downloaded the megauploadtoolbarsetup.exe file as root, so the file was only in /usr/local/apps/ie4linux/ie4linux/dosdevices/c:/windows/profiles/root/Desktop, and not in /usr/local/apps/ie4linux/ie4linux/dosdevices/c:/windows/profiles/myusername/Desktop.

Anyway, thanks for the tip, it felt so close, LOL. I hope I'll figure out how to bypass this... errr... megalimitation, oups, megaupload.com limitation. :D

---

### Post by jkeyes0 on 2007-02-28
I've used megaupload and never needed a toolbar. I've downloaded through firefox. The only problem is, it's limited download (300mb or something like that).

---

### Post by Zero.The.Hero on 2007-02-28
> **jkeyes0 said:**
> I've used megaupload and never needed a toolbar. I've downloaded through firefox. The only problem is, it's limited download (300mb or something like that).

I know it *should* be possible, but... aren't you being redirected to [**http://www.megaupload.com/toolbar/?**](**http://www.megaupload.com/toolbar/?**) ...with that stupid text, something like
> All download slots assigned to your country (xxxxxx) are currently in use. Please try again in a few hours or install the Megaupload Toolbar for immediate access - with the toolbar installed, there are no more slot limitations for you!




**Edit**
I remembered now: I think you're talking about megashares.com, as far as I recall they're the ones with the 300 MB download passport limit... I don't have any troubles at all with megashares.com, but with these stupid [bleep] megaupload.com guys !

---

### Post by jkeyes0 on 2007-02-28
I've used both, actually. I can just never keep them straight. I don't know if I've tried them since I went to linux, but I will this evening and see what happens (at work now, can't access the site from here)

---

### Post by Zero.The.Hero on 2007-02-28
> **jkeyes0 said:**
> I've used both, actually. I can just never keep them straight. I don't know if I've tried them since I went to linux, but I will this evening and see what happens (at work now, can't access the site from here)

OK, thanks :) I'll try as well some other... "maneuvres" and see if I can come up with something and keep you guys posted.

---

### Post by Esente on 2007-10-27
I probably bring up an old topic here, but just in case somebody need the answer, here is what I know:

Megaupload Toolbar offer Happy Hour, during which, you will become a premium member, provided that the toolbard is installed. It's quite good, really. So, in order to install that toolbar (don't get me wrong, I know it contains spyware, that's why it should only be installed inside Wine), run IE6 (by IE4Linux), from there, choose File from the menu, choose Open. Then select File type to All, choose toolbar.exe and run. It should work!

---

### Post by Baby Boy on 2007-11-06
I've been having problems with this damn Megaupload for months now and I finally got it to work with a very simple solution so I wanted to share it. Go [here]("https://addons.mozilla.org/en-US/firefox/addon/3843") and install the addon. Then restart Firefox and go Tools->Megaupload3->Enable. Works like a charm :popcorn:.

---

