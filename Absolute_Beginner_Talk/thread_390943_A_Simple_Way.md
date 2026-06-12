---
title: "A Simple Way"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-03-22
I am getting used to Ubuntu, having  been a Linspire user for years. With Linspire Internet Suite I was able to get mail notification, visual and audio and automatic checking for new mail. With Evolution I have to open the mail and send and recieve. Then I get a beep. Who needs a beep if you are already in the process of receiving your mail. I know how to set the beep or other wav files for notification, but it seems useless, when you have to open Evolution to do so. Is there a way to set up a mail notification, that will tell you in advance that you have mail before you open Evolution? If not will T-Bird do it? O do you just live with it. I have checked the forums but do not see a resaonable solution.

---

### Post by mcduck on 2007-03-22
Install the 'mail-notification'-package. It does exactly what you want.

---

### Post by rosswmcgee on 2007-03-22
Where is it located?

---

### Post by mcduck on 2007-03-22
It's in the Universe repository, so you need to enable that first. [http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

After that you can install it with Synaptic or 'sudo apt-get install mail-notification'.

To configure it go to System/Preferences/Mail Notification.

After that, when you have mail icon will appear in your Notification Area, and you can also set the Mail Notification to run a command when mail is received so you can set a command to play some audio file if you want (I'm using a command to light the mail led on my laptop instead).

---

### Post by rosswmcgee on 2007-03-22
OK! Now I have an icon in tool bar. If I put the mouse arrow on it, it says you have no new mail. If I double click on it Evolution opens, I click on send and recieve and 4 msgs were downloaded. Have I goofed here some where? Do I need to leave Evolution open?

---

### Post by rosswmcgee on 2007-03-22
I works and thank you!

---

