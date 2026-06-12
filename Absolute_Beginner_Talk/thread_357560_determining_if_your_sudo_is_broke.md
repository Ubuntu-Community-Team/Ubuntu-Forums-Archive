---
title: "determining if your sudo is broke?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Starry on 2007-02-09
ok so i followed all the directions in the previous thread: [http://www.ubuntuforums.org/showthread.php?t=353952 ]("http://www.ubuntuforums.org/showthread.php?t=353952") about installing flash 9 and it worked out fine until i got the very last part, as i said in that thread.

then i started looking at the actual coding and guessed that -su means sudo.  now being the smart person i am i did my entire unpackaging deal-io for flash as a root shell in a terminal as i followed those instuctions.  mind you this is the VERY FIRST THING i have ever done.  i thought i was doing pretty good.

now i went to the link about sudo being broken found on that page and thus far, it says that none of the commands can be found so i am hoping that it IS NOT broke but i have no idea.

for reference sake i am running debian 3.5  and i really want to get this flash installed to have a sense of accomplishment [and be able to do my taxes].

---

### Post by Maestro23 on 2007-02-09
1. Make sure the plugins directory is in /usr/lib/firefox first.

2. Try:

#sudo cp ibflashplayer.so flashplayer.xpt /usr/lib/firefox/plugins

You can also copy the files one at a time to the destination directory.

OR

You can get "flashplugin-nonfree" via Synaptic.  Its in the repositories.  Easier.

Remember to restart your browser once the plugin is installed.

---

### Post by optotron on 2007-02-09
and as for sudo being broke, I dont see how it could possibly be that.

the "su" command and the "sudo" are not quite tha same, su is used for changing user, while "sudo" is short for superuser do, and in case your sudo is broke, then you shouldn't be able to  use it, so it should be quite hard to fix it if that's the case (at least if your not used to the command line and booting to single user mode).

just typing $ su should switch your user to the superuser (root), but that is not possible because the root account is disables as per default under ubuntu linux.

if U need to do stuff as the root user rather than sudo, try $ sudo su or $sudo bash to get a root shell

---

### Post by Starry on 2007-02-09
> **Maestro23 said:**
> 1. Make sure the plugins directory is in /usr/lib/firefox first.

2. Try:

#sudo cp ibflashplayer.so flashplayer.xpt /usr/lib/firefox/plugins

You can also copy the files one at a time to the destination directory.

OR

You can get "flashplugin-nonfree" via Synaptic.  Its in the repositories.  Easier.

Remember to restart your browser once the plugin is installed.

ok the only thing in there is my java plug-in.

how do i get the flash one there?  i thought that was what i was doing....i typed in the command you gave me and nothing happened.  i'd rather do the easier thing lol but i don't know where the repositories are....

---

### Post by Maestro23 on 2007-02-09
> **Starry said:**
> ok the only thing in there is my java plug-in.

how do i get the flash one there?  i thought that was what i was doing.

If you use the "cp" command that I showed you, the files should copy there. Must be in the directory where the two files are first, then use the command. Again, if you are having trouble with the command line stuff right now, and you need flash in a hurry, get it via synaptic(GUI).

System &#8594; Administration &#8594; Synaptic Package Manager
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

Might have to enable some extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Hope I'm not confusing you...

---

### Post by Starry on 2007-02-09
> **optotron said:**
> and as for sudo being broke, I dont see how it could possibly be that.

the "su" command and the "sudo" are not quite tha same, su is used for changing user, while "sudo" is short for superuser do, and in case your sudo is broke, then you shouldn't be able to  use it, so it should be quite hard to fix it if that's the case (at least if your not used to the command line and booting to single user mode).

just typing $ su should switch your user to the superuser (root), but that is not possible because the root account is disables as per default under ubuntu linux.

if U need to do stuff as the root user rather than sudo, try $ sudo su or $sudo bash to get a root shell

ahh thanks for clearing that up.

i am doing everything as root, in a root shell.  i did pay some attention to doing linux stuff just never did anything with linux.  i know if i needed to update or change anything this was the way i had to do it.  so essentially am i being redundant in how i am typing things into the terminal?  is that the issue?  should i skip the #su part or -su part in the code line to solve the problem? since i am working as root?

---

### Post by Maestro23 on 2007-02-09
> **Starry said:**
> ahh thanks for clearing that up.

i am doing everything as root, in a root shell.  i did pay some attention to doing linux stuff just never did anything with linux.  i know if i needed to update or change anything this was the way i had to do it.  so essentially am i being redundant in how i am typing things into the terminal?  is that the issue?  should i skip the #su part or -su part in the code line to solve the problem? since i am working as root?

Just use "sudo". Easier and safer.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Starry on 2007-02-09
> **Maestro23 said:**
> If you use the "cp" command that I showed you, the files should copy there. Must be in the directory where the two files are first, then use the command. Again, if you are having trouble with the command line stuff right now, and you need flash in a hurry, get it via synaptic(GUI).

System &#8594; Administration &#8594; Synaptic Package Manager
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

Might have to enable some extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Hope I'm not confusing you...

oh i was confused a while ago LOL...

i didn't have any adobe flash installed at all so i had to start from scratch and mind you this is the FIRST thing i have ever done.  i'm learning just like everyone else in this section.  i'm trying though.

as i said, everything worked right up to the last two lines of code from here: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)[http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")

[CENTER]sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/[/CENTER]

why i thought it might have something to do with sudo and i started looking at sudo in the first place.  otherwise it all worked.  i'm sorry if i am just repeating myself....i can get lost in a paper cup.

---

### Post by Maestro23 on 2007-02-09
No prob man.  We all have been there... but it is fun when you fix something.:) And this is the best forum for a distro I have ever been a part of.  Friendly and very helpful.

So, is flash working for you now?

---

### Post by Starry on 2007-02-09
> **Maestro23 said:**
> No prob man.  We all have been there... but it is fun when you fix something.:) 

So, is flash working for you now?

nope i haven't gotten the thing moved yet.   i am still stuck on that part, and that sudo thing.  i have determined that its not broke at least heh.

how i am determining if my flash is working yet is by going to a site i know needs flash and it keeps telling me that i need it.  however, my icon for firefox on my desktop did change itself, the icons inside it changed as well as the countdown timer.  i've done something obviously but the plugin hasn't stuck because its not in the folder for firefox.

ugh.  where have i gone wrong?  i also cleared my cache to even see if that was an issue earlier.  i am still in recovery mode too just an FYI.

---

### Post by Maestro23 on 2007-02-09
In what directory are the two files you need at?  Get to that directory and use the command I posted earlier.

---

### Post by Starry on 2007-02-09
they were in the file on my desktop but i moved them out of the file onto the desktop thinking i could just drop them into the firefox folder that they needed to go in but i couldn't do that.

so now they are just sitting there.  but i found them lol.

and the two files that are missing from the entire setup is flashplayer.xpt and libflashplayer.so  [but i think you know that] and the file that they are going to is called mozilla-firefox not just firefox, i have two...but everything is in the mozilla one.

i tried to move them using the cu command again you gave me but it just gave me a blank line and did nothing.

---

### Post by Maestro23 on 2007-02-09
> **Starry said:**
> they were in the file on my desktop but i moved them out of the file onto the desktop thinking i could just drop them into the firefox folder that they needed to go in but i couldn't do that.

so now they are just sitting there.  but i found them lol.

and the two files that are missing from the entire setup is flashplayer.xpt and libflashplayer.so  [but i think you know that] and the file that they are going to is called mozilla-firefox not just firefox, i have two...but everything is in the mozilla one.

i tried to move them using the cu command again you gave me but it just gave me a blank line and did nothing.

If the command was successful, you will get a blank line. Have you checked the plugin directory?

---

### Post by Starry on 2007-02-09
they aren't there.  not in the plugins or in the other part of the folder.  they are still sitting in the folder on the desktop.

this is the error i am getting now

# sudo cp libflashplayer.so flashplayer.xpt /usr/lib/mozilla-firefox/plugins
cp: cannot stat `libflashplayer.so': No such file or directory
cp: cannot stat `flashplayer.xpt': No such file or directory

---

### Post by Maestro23 on 2007-02-09
> **Starry said:**
> they aren't there.  not in the plugins or in the other part of the folder.  they are still sitting in the folder on the desktop.

this is the error i am getting now

# sudo cp libflashplayer.so flashplayer.xpt /usr/lib/mozilla-firefox/plugins
cp: cannot stat `libflashplayer.so': No such file or directory
cp: cannot stat `flashplayer.xpt': No such file or directory

In your terminal when you run the command, are you in: [COLOR="Red"]/home/user/Desktop[/COLOR]  since that is where the files are at?

User = user name you logged in with

---

### Post by Starry on 2007-02-09
i believe so.  i went to the desktop, opened a terminal and am doing it from there.  a root shell like i have been from the get go as root.  i tried it from the normal shell and they still didn't move though but i didn't get the error message.

---

### Post by Maestro23 on 2007-02-09
> **Starry said:**
> i believe so.  i went to the desktop, opened a terminal and am doing it from there.  a root shell like i have been from the get go as root.  i tried it from the normal shell and they still didn't move though but i didn't get the error message.

What do you see when you type:

#pwd

Will tell you where you currently are at.

---

### Post by Starry on 2007-02-09
home/star  so yes i have been where you asked.

i feel like i am wasting your time...i really appreciate you taking it to help me i just wanted to say that.

---

### Post by Maestro23 on 2007-02-09
> **Starry said:**
> home/star  so yes i have been where you asked.

i feel like i am wasting your time...i really appreciate you taking it to help me i just wanted to say that.

No prob man. If the files are on your desktop, then you are not where you need to be.  The output from that command should be:

/home/star/Desktop

Type this:
#cd Desktop
#ls 
Should see everything that is on your Desktop.

---

### Post by Starry on 2007-02-09
starry:~/Desktop# Is
-su: Is: command not found

uhhhh....now what?  heh.

---

### Post by Maestro23 on 2007-02-09
> **Starry said:**
> starry:~/Desktop# Is
-su: Is: command not found

uhhhh....now what?  heh.

sorry: lower-case L

#ls

---

### Post by Starry on 2007-02-09
Home.desktop  trash.desktop


that doesn't seem right.....i have files on my desktop but no programs per se.

---

### Post by Starry on 2007-02-10
i've been plugging away at this still after taking a break and i still can't get anywhere with it.  i've taken the two files out of the folder to try and move them via the cp command but i get the no such file or directory error nor are they on my desktop using the #ls function either.

anyone?  bueller?

---

### Post by Maestro23 on 2007-02-10
> **Starry said:**
> i've been plugging away at this still after taking a break and i still can't get anywhere with it.  i've taken the two files out of the folder to try and move them via the cp command but i get the no such file or directory error nor are they on my desktop using the #ls function either.

anyone?  bueller?

This is strange.  I have tested every command I have given you on my system with no probs.  Are you using sudo?  You are not still using straight root are you?

Have you tried getting it via Synaptic like I said in an earlier post?

---

### Post by Starry on 2007-02-10
yeah sudo is fine, no problems.  i'll do it in the root window and if i get a problem i'll do it with the sudo in the other terminal window the longer way to see if thats the issue and sometimes it is sometimes its not.  the files just REFUSE to move.

i have no idea what that synaptic stuff is, its all greek to me.  i keep re-reading this all over and trying different stuff but getting no where.

should i just start over again from the very beginning?  just let it go and see if i get the very same error?

---

