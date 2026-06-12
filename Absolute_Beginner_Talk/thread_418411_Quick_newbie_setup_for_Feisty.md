---
title: "Quick newbie setup for Feisty"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Michaelt74 on 2007-04-22
A quick setup guide that may help newbies, all this info is from the forum posts I've found and from the Ubuntu documentation provided.:

[B]Make the fonts in Ubuntu appear similar to the Windows XP fonts (less strain on the eyes)
[/B]
Install msttcorefonts (System>Administration>Synaptic Package Manager> search for msttcorefonts and install these. Next follow the guide using the following link:

[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

Remember to reboot for the settings to take effect.

**Multimedia codecs**

Something which caused anguish in the past has been made simple.

Click on Applications>Add/Remove Applications>search for Ubuntu Restricted extras, install these. You will now have most the of the codecs needed to play streaming video and audio. In the same application, search for and install the Flash plugin. Search for and install the VLC Media Player, I found this the most useful and reliable media player to use, especially for streaming.

**Firefox media streaming**

Search for and install the media player connectivity add on in Firefox:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

When it’s installed use the wizard and configure VLC to play all streaming video.

*Note I encountered a problem which resulted in degraded quality when I stream video from Yahoo using VLC, fortunately I found a fix; this may or may not work for you. When you open a link to streaming content from Yahoo, click on ‘Video Quality’, the option next to ‘help’ (your current preference / detected streaming rate is displayed). Mine is 300k. Click on 100k, then ’select’, an advert may reappear, when it’s finished, click on ‘Video Quality’ again and select your original settin (mine was 300k so I clicked it again), then ’select’. When you click on the small ‘play button’ the quality should be greatly improved.

[B]Mount Windows and enable write access to the Windows partition (for users dual booting between Windows XP and Ubuntu)
[/B]
This is straight forward, follow the instructions on this link:

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html)

The instructions indicate they are for Edgy 6.10, but they work fine in Feisty 7.04. Next, click on System>Administration>Synaptic Package Manager> search for and install NTFS CONFIG (an application which enable write access to the Windows partition). When NTFS CONFIG is installed, click on Applications>System Tools>NTFS configuration tool, check ‘Enable write support for internal device’, if you share Windows and Ubuntu on the same hard drive.

---

### Post by raja on 2007-04-22
Looks like that must be OK for most users. I would think however, that instead of mostly providing links or instructing to search in synaptic, you should provide commands that can be pasted in the terminal. That would be pretty simple to do - both for you and the user who wants to get the application.

---

