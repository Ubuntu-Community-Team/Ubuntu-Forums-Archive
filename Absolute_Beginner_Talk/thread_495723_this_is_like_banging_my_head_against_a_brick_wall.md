---
title: "this is like banging my head against a brick wall"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by leetj on 2007-07-08
hi i am a ubuntu user 1 and a 1/2 days old 
i have for the last 15 hrs been  trying to install either 1) vmware   2) virtual box .  with no results at all , i followed the tutorial that i found here for vmware [http://ubuntuforums.org/showthread.php?t=183209](http://ubuntuforums.org/showthread.php?t=183209)
but no joy it did not work ,even followd it word for word

i have reinstalled the OS 3 times to try again from clean start   no joy 
i also tried to install virtual box by using the package manager ,now this was a download from their site with   ubuntu(feisty) virtual box i386 deb
now this seems to be working ok then says that it is installing and just hangs forever

so next i download it again and this time copy to disk ,so the icon is on my desktop,  i click on it  and it opens package manager ,put in my password  then click on install , then i gives me a new box that says 'only one management tool can run at the same time' and suggests i should close one of the following; update manager,aptitude manager,synaptic manager ,and unless i do it wont continue    but were are either of these running , i do not know !

but the thing is non of these are open  ,so i reboot and try again --------------->but same result as above
i am using ubuntu 7.04 with all latest updates  i am gonna give it one more shot if anyone can help me , 
because i feel i have just waisted a day of my life tryin to get a VM to install on a system that claims to be not just for geeks     sorry but an operating system should be user friendly and linux 
'simply' (15 hrs and nothing installed, XX diferent how to's to launch an app)   is not .
but i really wanna keep at it  and learn,  but i need windows xp for important software that i use
can anyone  help me my head is sore but the wall still stands!
for any response i am indepted
tx ,lee

---

### Post by starcraft.man on 2007-07-08
Ok... follow me now, deep breath. In *breathe* and out *exhale*.

Feel better now? :)

Ok, gonna get this sorted. First, lets forget about VMware and the guide. I dunno if you've messed anything up with your install of Ubuntu, when in doubt I'd recommend a clean install. Anyway, now to installing Virtual Box.

1) We are not going to use the deb installer. I prefer the repository. So, please bear with me, the first and most essential step is opening the command line. Applications > Accessories > Terminal.

2) With the terminal open, please open your sources list. This of course is the place where you store information that tells Aptitude (your install program) where to look for and retrieve programs to install. Each line corresponds to a repository, which is really just a server that houses the packages/software that is installed on your computer. Now to open sources list input this command:

```
gksudo gedit /etc/apt/sources.list
```

3) With that open, you will see lots of lines, scroll to the bottom and add this line to it:

```
# Virtual Box
deb http://www.virtualbox.org/debian feisty non-free
```

Then save and exit.

4) Now we have to add the key to access it, Virtual Box of course provides this to the public. Keys are used as a means of authentication, all of them are freely available to people. Issue this command to the terminal:

```
wget -q [COLOR="Blue"]http://www.virtualbox.org/debian/innotek.asc[/COLOR] -O- | sudo apt-key add -
```

This command can be used to import any key, if you add lots of separate repos you will find it handy to keep somewhere. Just replace the blue line with the url of the key and it will always work.

5) Now that we have the repository and the key to it, we have to refresh the list.

```
sudo apt-get update
```

6) Finally, with the list refreshed we can install virtual box with one single command.

```
sudo aptitude install virtualbox
```

And your there. If any error is returned when trying to install virtual box please post it here. Otherwise, you should have a perfectly working copy. Any questions, post back.

For more on terminal: [URL="http://www.linuxcommand.org/"]Linux Command
[/URL]

---

