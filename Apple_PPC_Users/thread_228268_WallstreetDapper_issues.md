---
title: "Wallstreet/Dapper issues"
date: 2006-08-02
forum: Apple PPC Users
---

### Post by briandtaylor on 2006-08-02
I've just installed via an 'alternate' install disc, due to my low 160 mb of ram. I have finally (after the 3rd try) gotten everything together and have been given the ubuntu login screen. after logging in, the splash screen with the various systems loading does display, but then I get an error that "nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem." and also "There was an error starting the Gnome Sttings Daemon. Some things, such as thems, sounds, or background settings may not work correctly. The Setting Daemon restarted too many times. The last error message was: System exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0" and also "There was a problem registering the panel with the bonobo-activation-server. THe error code is: 3. The panel will now exit.
Then, i have black screen, with just the mouse pointer to play with. When i unplugged the power cable, it did alert me that it was now using battery power, however...

does this mean my installation wasn't as successful as I thought? is there a way to come back from these errors?

thanks in advance, and remember that i am a newbie and need more explanation than most, probably.


--brian

---

### Post by avtolle on 2006-08-03
[http://www.ubuntuforums.org/showthread.php?t=199107&highlight=Wallstreet](http://www.ubuntuforums.org/showthread.php?t=199107&highlight=Wallstreet) is a thread which may give you more information. See especially post #7. As you may pick up by reading through the thread, it is necessary to use Boot-X to boot Ubuntu on an Old World Mac, which, by your general description, is what I divine to be your situation. Also, there is a link in the thread to a Wiki article that I believe will be helpful. HTH.

---

### Post by briandtaylor on 2006-08-04
thanks for your reply---------------------
i've decided that perhaps starting with xubuntu might be a better option, as I don't have the necessary code base to be able to manipulate the full dapper installation. i am having the same problem that i had with the full dapper installation disc-the file directory is different than that of the alternate disc. if I look on the alternate cd, there is a folder called install which has the ramdisk file and the vmlinux file. on the full dapper and the xubuntu ones, they are located in a folder called 'casper,' but they won't work in the same fashion as the alternate install. If i copy those files into the proper locations for boox-x, i get not very far into the install boot and it says it can't find what it needs...then goes to a shell script. are there bonafide instructions somewhere that includes the *new* locations of the linux kernel and ramdisk file?

---

