---
title: "[SOLVED] Keyring"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2007-12-06
I don't get this keyring thing. Is there a very basic explanation of this somewhere that will walk me through it like I'm 5 years old?

I am asking because when I connect to my WPA wireless network, not only do I have to enter the wireless password every time, I have to enter the default keyring password. I don't remember setting one up, and it doesn't take my user password. So I don't know what to type. I hit deny which works, but as my connection fades in and out it's very annoying to have to deal with this all the time.

Or if there's a way to sidestep this problem, that would be fine.

Thanks for any help!

---

### Post by p_quarles on 2007-12-07
The Gnome Keyring is an application that encrypts and stores password and passphrases for you. It asks for this when you connect because it assumes you will want to use the keyring instead of manually typing the entire WPA passphrase each time you connect. 

Basically, next time you connect, try setting up the keyring password (it can be the same as your user password) and instruct it to remember your WPA passphrase. It's been a while since I've done this myself, so I can't remember the exact steps, but I remember it being very intuitive once you've set the keyring password. 

Once you load the keyring, it stays loaded for the rest of the session. So, if your wireless drops, you'll be able to reconnect to your router without re-entering the password.

Also, there is a way of getting the keyring to load automatically, without prompting for a password. It is apparently buggy in the current version of Ubuntu, but the following link explains how it works (and a bunch of other stuff related to your question):
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28keyring%29](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28keyring%29)

---

### Post by dinostabOMG on 2007-12-07
Thanks for the response

> **p_quarles said:**
> 
Basically, next time you connect, try setting up the keyring password (it can be the same as your user password) and instruct it to remember your WPA passphrase. It's been a while since I've done this myself, so I can't remember the exact steps, but I remember it being very intuitive once you've set the keyring password. 

This is the part I'm having trouble with. When I connect to the network, this is what I get
[IMG]http://i210.photobucket.com/albums/bb69/joentdothat/Screenshot.png[/IMG]

From what I can tell: my choices are Deny and OK, and that's it. Regardless of what I type into the box, if I hit OK it just comes up again. If I type nothing, it tells me it can't be blank. If I hit deny it goes away, but just until the next time. I would really like to set up the keyring password, but HOW?

This must be something strange that's only happening to me because nobody else seems to have so much trouble with this, but it has happened on two clean installs on two different computers.

I've gone into the keyring manager, but I don't know what to do from there...

---

### Post by p_quarles on 2007-12-07
It's been a while since I've used Gnome for my desktop, so I'm trying to remember exactly how the keyring manager works. Could you open it up and post a screenshot of that?

---

### Post by dinostabOMG on 2007-12-07
[IMG]http://i210.photobucket.com/albums/bb69/joentdothat/Screenshot-sessionKeyring.png[/IMG]

When I open the keyring manager, I got the same prompt saying "Enter default password for keyring to unlock." Same problem, I don't know what to type. This happens again if I click login in the right pane, with the silver shield. When I say Deny I get an error: "Access denied to keyring."

I clicked View -> keyrings to open that left pane. The Keyring menu has New Keyring, Delete Key, and Delete Keyring. I was able to create a new keyring, and it would accept the password I gave it. However, this didn't solve my wireless problem at all. I deleted it subsequently with no problem.

---

### Post by p_quarles on 2007-12-07
> **dinostabOMG said:**
> When I open the keyring manager, I got the same prompt saying "Enter default password for keyring to unlock." Same problem, I don't know what to type. This happens again if I click login in the right pane, with the silver shield. When I say Deny I get an error: "Access denied to keyring."

I clicked View -> keyrings to open that left pane. The Keyring menu has New Keyring, Delete Key, and Delete Keyring. I was able to create a new keyring, and it would accept the password I gave it. However, this didn't solve my wireless problem at all. I deleted it subsequently with no problem.
Okay, I think I found a solution via the magic of Google. I figured there must be a way of nuking the current keyring password and starting over (and it looks like that's what you need to do). Basically, just delete the "default.keyring" file in /home/username/.gnome2/keyrings/ 

Step by step instructions here:
[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

I think that will work, but if it doesn't, you can then try reinstalling the keyring manager and the network manager.

---

### Post by dinostabOMG on 2007-12-07
Thanks! I will try that when I'm back on my machine.

Nevertheless, how did it get that way in the first place? This is a clean install, I don't know what I might have done to instigate this situation. Plus it happened on two computers, the one in question (a 64-bit desktop) and a 32-bit laptop running Feisty.

Academic at this point if it works, but still, weird. I'll let you know.

---

### Post by dinostabOMG on 2007-12-09
Interesting - I don't have a default.keyring file. I do, however, have a logon.keyring file. I moved it to my desktop for backup. The next time I connected to my wireless network, though, I was prompted to create the password. In that folder, default.keyring has been created. Thank you! This seems to have done it.

---

### Post by dinostabOMG on 2007-12-15
One last thing, just for academic reasons. Why would this have happened? It happened with two completely clean installs, why should this have become necessary?

---

