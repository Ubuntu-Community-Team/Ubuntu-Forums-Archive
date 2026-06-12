---
title: "new user, old problems"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by leviticusforjesus on 2008-03-27
i need help to get my wireless network on 8.10
i have it on the drive but it wont apply or come on at start up
help mentioned "ndisgtk" but it wasnt in the place it said it was

---

### Post by iansane on 2008-03-27
it's in synaptic. Don't know if it is from restricted universe or multiverse repos. I have those enabled. 
If you enable them then do "sudo apt-get update" in terminal or you can just do it all from synaptic. Then see if it shows up.

---

### Post by leviticusforjesus on 2008-03-27
problem is that i have to be on windows to get online,
and i have to switch back and forth which means a reboot each time:(
ill go try it though. thanks

---

### Post by iansane on 2008-03-27
I should have specified, go to sytem>admin>synaptic, then in synaptic go to settings>repositories and check the boxes to enable the restricted, universe, and multiverse repositories. You'll have to click reload afterwards and then search for it

---

### Post by iansane on 2008-03-27
> **leviticusforjesus said:**
> problem is that i have to be on windows to get online,
and i have to switch back and forth which means a reboot each time:(
ill go try it though. thanks

You say your a new user so it may be a little complicated figuring out ndisgtk. I haven't had the pleasure of needing it yet luckily so I know nothing about it but a lot of people on the forums can help with it if you run into trouble.

---

### Post by leviticusforjesus on 2008-03-27
ok swithing systems to try ill let u know how it goes

---

### Post by leviticusforjesus on 2008-03-27
total pain! what you had me do is for downloading from the web but the problem is that my wireless card wont turn on to do that, im lost now.
also i have the wireless driver on a disk an i though to try installing it to 8.10 but it wont run

---

### Post by iansane on 2008-03-27
Oh crap! I am so sorry. I feel like a total idiot now. I should have thought that through more before I replied.

Hopefully someone can tell you how to download the package on windows and transfer it over. I'm looking for it now but no luck yet.

---

### Post by kesman on 2008-03-27
Is it impossible for OP to hook up a wired connection to that pc and work with it? Also, where did you get Ubuntu 8.10? :O

---

### Post by iansane on 2008-03-27
OK if you are using gutsy, go here
[http://packages.ubuntu.com/gutsy/i386/ndisgtk/download](http://packages.ubuntu.com/gutsy/i386/ndisgtk/download)

If it's another distro, they have them here.

[http://packages.ubuntu.com/gutsy/net/ndisgtk](http://packages.ubuntu.com/gutsy/net/ndisgtk)   Just choose your distro and 64 or i386. At the bottom under "download ndisgtk"

 click on a mirror to get the deb package which you can transfer over on a thumbdrive. When you click on it to install it should tell you if there are other dependencies. hopefully there won't be but if so, I assume you could find them at the same place.

As far as installing your driver to the ndis wrapper, (ithink that's how it works), I don't know but others here do. Once you get the .deb packages installed, make a new post if you need help with that part. It'll get read and responded to more. Once again, I'm sorry for messing you up the first time

---

### Post by iansane on 2008-03-27
> **kesman said:**
> Is it impossible for OP to hook up a wired connection to that pc and work with it? Also, where did you get Ubuntu 8.10? :O

Well it's either gutsy or hardy. LOL 

I guess that would be another alternative if there is a wired NIC card or a slot to put one in. I'm about to do that for windows server 64 because unlike Ubuntu, they can't provide drivers for my onboard nvidia LAN.

---

