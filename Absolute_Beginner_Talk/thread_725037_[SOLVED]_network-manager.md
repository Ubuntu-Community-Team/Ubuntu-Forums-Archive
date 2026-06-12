---
title: "[SOLVED] network-manager"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-03-15
Hi,

I've (at last!) managed to install my wireless card and I installed wifi radar.

I can successfully see my wireless router but I am unable to connect (i think) as I don't think I'm able to fill in the correct setting. I've tried a few combinations.

I noticed on other posts that GNOME network manager may be easier to use?!

My laptop is non internet or ethernet at the moment so I'm having to transfer packages manually.

network-manager-gnome wont install until I have libavahi-glib installde (it tells me) and this wont install until I have libc6. However I do have libc6! and If i try t install that it tells me i already have it.

Can anyone point me in the right direction of how to get this instaled please? or how to get wifi radar configured? 

Thanks

---

### Post by forrestcupp on 2008-03-15
You may still have to enter your security code if you have a secured wireless connection.

---

### Post by glennric on 2008-03-15
You will need to download network-manager-gnome and all of its dependencies that are not installed on your computer.  This could take some work as the dependencies could have dependencies of their own.   As to the libc6 issue, you could try downloading the libc6 debian package and typing 
```
sudo dpkg -i libc6_*.deb
```
in the directory that you download it to.  

Do you have any way to connect the computer to a wired network?  That would be the best way to do this.

---

### Post by hyperair on 2008-03-15
EDIT: Nevermind, stupid question.

---

### Post by the beak on 2008-03-15
I'm afraid not i have no access until I get the wireless working.

I've installed libc6 and it still come up with:

error:dependency is not satifiable: libc6 

when trying to install libavahi-glib1

???

---

### Post by the beak on 2008-03-15
PS I've tried it with the security and it doesnt work

---

### Post by glennric on 2008-03-15
It sounds like you have something more serious wrong with your computer.  Linux can't run with out libc6 installed.  By the sound of it it is, but the installation is corrupt.  Did you try getting the libc6 package and doing what I said?  You do have a way to copy files to that computer don't you?  If not there really is no hope.

---

### Post by the beak on 2008-03-15
I restored libc6 and downloaded and put WICD on my machine instead.

I love it, I'm now on the net. YES!

Thanks people.

---

### Post by forrestcupp on 2008-03-15
Thanks for posting your solution.

---

