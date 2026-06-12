---
title: "Software Update Manager - Warning ?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-02-25
I have just been informed that there is a software update available for me ....... but I have not downloaded this as I was unsure ........... **can someone clarify for me if it is safe to do so**?

Thanks :)

[IMG]http://1pix.org/out.php/i545_Untitled.png[/IMG]

[IMG]http://1pix.org/out.php/i546_Untitled2.png[/IMG]

---

### Post by chewearn on 2007-02-26
This happened to me quite frequently.  What I normally did is to cancel the update.

Then, open up Synaptic Package Manager; then click on Reload, Upgrade and Apply.  Most of the time, the warning went away.  If it didn't, I waited for the next day and try again.

---

### Post by chrome307 on 2007-02-26
Thanks for the advice  **Astalavista**

Being a new user .......... I seem to erring on the side of caution :)

I will try your suggestion and hopefully it will work

---

### Post by TonKi on 2007-02-26
This is not an official ubuntu update it's from a third party source that you or automatix added and is not authenticated. The warning wont go away ;)


To get ride of the warning you have to add his trusted key, with the following command(s)
```
wget http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -
wget http://givre.cabspace.com/ubuntu/givre_key.asc -O- | sudo apt-key add -
```

[Givrés repository]("http://flomertens.keo.in/ubuntu/")

btw its safe to do :)

---

### Post by carverj on 2007-02-26
Don't worry, the Linux world is unlike the Windows world in that respect.
That's why many don't bother with antivirus and antispyware and is why I moved to Linux as my main OS!
We got sick of all the attacks on the Windows OS 4 years ago and so switched.
I have not had any incidents since!!
:)

---

### Post by chrome307 on 2007-02-26
Well I did download this and have now realised my Kingston USB Flash Memory stick is not being recognised :(

Is there a way to unistall this update ??

As I use the FlashMemory stick to transfer files - so it's really important for me.

Thanks

---

### Post by TonKi on 2007-02-26
```
sudo apt-get remove pmount
```
or you can start up synaptic and remove it in there

---

