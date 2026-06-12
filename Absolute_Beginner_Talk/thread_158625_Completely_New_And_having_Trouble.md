---
title: "Completely New And having Trouble"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by Drathorin on 2006-04-11
I just got ubuntu yesterday, and I have a slight problem.

I am currently on dial-up, and my modem is a winmodem, as such I can't get online in Ubuntu.  So I downloaded the driver for it as a DEB file (I'm dual booting right now, which is why I'm able to be online)

I tried installing the DEB file, but I kept getting password errors and all sorts of runarounds (This is my first time running Linux, I'm a old windows user)

I was told to get Synapsis, and I downloaded it and ran it using this command line

"sudo dpkg --install synapsis.deb" (I renamed the synapsis downloaded file)


And I still can't seem to use the GUI to extract the modem drivers. And I can't seem to run synapsis itself. It asks for the root password, and I give it, but it asks for my 'keychain' password. So I just enter the root again, But no dice.

Any help would be appreciated. . . Though I'm wondering if I'm not computer literate enough to use this OS. . .

---

### Post by nalmeth on 2006-04-11
Sorry, I've never setup a modem personally so I can't directly help you. Assuming that your modem is supported in linux, your literacy shouldn't matter too much.
A lot of the problems you will run into can be solved with ubuntu's excellent documentation. Following howto's and troubleshooters will help tremendously, and if you have problems with some of the steps in the docs, these forums are great at lending a hand. Just post all the related info, like the model name of your modem in this case. 
Have you checked this out yet? It may give you some good info:
[https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")
wiki.ubuntu has a lot of great howtos.
another great site is:
[http://doc.gwos.org/index.php/Main_Page]("http://doc.gwos.org/index.php/Main_Page")

If you get stuck somewhere just post your hardware and the step you're trying to take, and someone who actually knows will likely help. 

Good luck

BTW I think that keychain is a way to setup one password to give access to all others saved in the keychain, or something along those lines. Did you ever set anything up like that?

---

### Post by steve.horsley on 2006-04-11
Unless you did an expert install, the password it's looking for is your password, not the root account password. Looky here... [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

I have never seen anything ask for my keychain password. 

Good luck with the modem driver. It's years since I did one of them, and I really don't remember the details. I did have to compile something though.

---

