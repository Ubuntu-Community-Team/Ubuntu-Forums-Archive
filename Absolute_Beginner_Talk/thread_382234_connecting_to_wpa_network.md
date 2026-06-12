---
title: "connecting to wpa network"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by gameman12 on 2007-03-11
hello all,

i'm trying to connect to a wpa secured wireless network, but it doesn't show the network in the network manager. what does that mean and how can i fix it?

thx for helping

---

### Post by kelbizzle on 2007-03-12
Maybe the essid is hidden? I know even before I configured NM-applet to work with wpa, the networks still showed up. I just wasn't able to connect to them. 2.4 Ghz interference from a cordless phone could be an issue.

---

### Post by siciliancasanova on 2007-03-12
From what I understand you can't connect to wpa by default in ubuntu.

I think you need to use a program like **wpa_supplicant** to make it work for wpa connections.

If no one answers your question in this thread, the people in the **networking/wireless **forum would know for sure.

**EDIT:**  Here is the link to wpa supplicant [wpa_supplicant]("http://hostap.epitest.fi/wpa_supplicant/")

---

### Post by gameman12 on 2007-03-12
thx, i will try wpa supplicant, but should i also try using wifi radar? i've hearded it helped others with similar problems

---

### Post by Drate on 2007-03-12
wpa supplicant is installed by default in Edgy.  Do you have the network manager icon in your little app tray thingy up top?  If so, left click on it, should be two options that say something to the effect of: connect to other wireless networks or create new wirelss network, you'd want the first... 

also, what kind of wireless network card are you using? I've spent a lot of time working out these problems with a Linksys Wireless-G with Speed booster.  If that's what you have then go here: [http://ubuntuforums.org/showthread.php?t=381770](http://ubuntuforums.org/showthread.php?t=381770)

That's how I got my card working from ground up... so give us back some info on your system and hardware configuration, I think we'll be able to better diagnose and help with your problem.

---

### Post by gameman12 on 2007-03-12
great thx. exactly what i am having trouble with. i actually have a standaard wirless g router (linksys) i am using ndiswrapper for the infamous  broadcom 4306 wireless card on a dell laptop.  i'm curretnly wired into a my cable modem, which is extremly inconvient. i am trying wifi radaar with no lulck so i am going to uninstall it and put net manager back on and use ur thread 'cause i have a similar situation. i won't be back for a few because i need to reconnect my router to the modem.

i just re installed net manager to find that i do not have the option of connecting to  a wireless network.....i'm gonna tinker with that for a while but if anyboyd could help i'd appreciate it

---

### Post by gameman12 on 2007-03-12
DRATE THANK YOU SO MUCH!!!!!!

i just used the link in ur post and it worked perfectly!!!!!!! i'm curretnly posting this from my wireless connection. my network manager is working fine now.

Drate, thanks again so much, u've been a huge help!!!



thnks again
:guitar:

---

### Post by Drate on 2007-03-12
You have no idea what kind of warm fuzzy you just gave me... I did something right!

Well good job on your new wireless connection.

I'm going to go revel in the radiating glow of usefulness for a bit... *sigh* :KS

---

