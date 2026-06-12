---
title: "I erased my hostname...HELP!"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by boogieman on 2006-02-07
I really screwed up big time.  Here's how:

I clicked on 'System' then 'Administration' then 'Networking' because I can't get my wireless USB (Linksys) adapter to work.  But I'll save that for another post.

In the Networking box (now this part is from memory), I clicked the second tab that had my hostname in it.  In one of my many moments of "Let me change this and see if it works," I erased the hostname.  Now the fun begins.

Didn't really know I had a problem till the next time I booted it up.  At bootup I get, "Could not look up internet address for .  This will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding to the file /etc/hosts."  Click 'Log in anyway' and I'm in.

When I pull up a terminal, I get: andrew@:~$

When I type sudo (something here)  I get: sudo: unable to lookup via gethostbyname()

Of course I'm brand spanking new at this, and appreciate any help.

---

### Post by taurus on 2006-02-07
At the prompt, use a text editor and create it like

sudo pico /etc/hosts

Then, add this line to it

127.0.0.1     localhost.localdomain localhost

Save it and reboot...

---

### Post by Packard Dell on 2006-02-07
can you tell me what is exactly the word after the *"Could not look up internet address for ...*? is it something like **x1-6-00-14-blah-blah-blah** or similar to that? Ok, take a note of that word then do the following:

1. from terminal, type **sudo gedit /etc/hosts** then press [ENTER}
2. place your cursor at the very end of the word **localhost** from the line *127.0.0.1	localhost.localdomain	localhost*
3. press [TAB] key then type in the word that i told you to take note. Or i think you can instead type in what was your hostname before (might be a better option) rather than the **x1-6-00-14-blah-blah-blah**. just do a trial and error.
4. save it and close gedit.
5. log out and log back in, you might not get that error anymore.

goodluck! let me know if that solves your problem.

---

### Post by boogieman on 2006-02-07
I forgot to mention the most important point.  I'm not able to get back into  Networking under the Administrator menu.  When I click on Networking, it thinks for a few seconds and does nothing.

The error message at bootup does not show anything.  It says "Could not look up internet address for ."

I'm not sure I understand the text editing post, Taurus.  Where do I type 'sudo pico /etc/hosts'?

If I type anything in a terminal it says 'sudo: unable to lookup  via gethostbyname ()'

---

### Post by boogieman on 2006-02-07
Oh, and when I open the hosts file it's read only.

---

### Post by Packard Dell on 2006-02-07
post what is exactly in you*r /etc/hosts* file if you can.

> I'm not sure I understand the text editing post, Taurus. Where do I type 'sudo pico /etc/hosts'?
type that from the terminal to open up your */etc/hosts* is probably what he meant.

> Oh, and when I open the hosts file it's read only.
it is read only and you cannot modify it because you probably double clicked it to open that file. in order to modify that, use **sudo** command but since you're having problem with sudo, i don't know any alternative way.

i had also similar problem like that in Fedora Core 4, the above steps i gave you have solved it

---

### Post by Packard Dell on 2006-02-07
or try to create another username from *System > Administration > Users and Group*, log out then log in using your newly created username.

---

### Post by boogieman on 2006-02-07
/etc/hosts file:

127.0.0.1 localhost.localdomain.localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by boogieman on 2006-02-07
I cannot select anything under System->Administration.

Whatever I pick, it'll show for maybe 5 seconds at the bottom of the screen while the computer's thinking, then it disappears.

---

### Post by Packard Dell on 2006-02-07
[QUOTE=boogieman]/etc/hosts file:

127.0.0.1 localhost.localdomain.localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/QUOTE]

ok, edit the line **127.0.0.1 localhost.localdomain.localhost** [COLOR="Red"](but are you sure that a dot (.) is separating between the **localdomain** and the second or last **localhost**? should be a tab space in between them)[/COLOR], and then type in your username. after appending that line, it will look like this:
> 127.0.0.1 localhost.localdomain localhost  your_username
just go back to my recent post and follow the steps i've given you. let me know when you got it work.

---

### Post by boogieman on 2006-02-07
Sorry...there's no dot there, only a space.  I had to take a picture of it and hand type it all in.

I'm not able to edit any documents.  I cannot do what you said.

---

### Post by Packard Dell on 2006-02-07
[QUOTE=boogieman]I cannot select anything under System->Administration.

Whatever I pick, it'll show for maybe 5 seconds at the bottom of the screen while the computer's thinking, then it disappears.[/QUOTE]

yeah coz your GNOME might not working properly now. try to search how can you create a new user from run-level 3 (no GUI or X windows). another option is that, boot from your installation cd then type in **linux rescue** from the prompt, but i can't give you any further commands for that though, sorry.

---

### Post by boogieman on 2006-02-07
Thanks a million.  I'm gonna try that.  If it doesn't work, guess I'll have to do a reinstall.

This is so much fun!!!  (<-not sarcasm)

---

### Post by Packard Dell on 2006-02-07
[QUOTE=boogieman]Thanks a million. I'm gonna try that. If it doesn't work, guess I'll have to do a reinstall.

This is so much fun!!! (<-not sarcasm)[/QUOTE]

ok, i've just found this [http://www.linuxhomenetworking.com/linux-hn/addusers.htm#_Toc92808557]("http://www.linuxhomenetworking.com/linux-hn/addusers.htm#_Toc92808557")
on how can you add new user, i didn't read it through but it might help. well, if you're still having problem, yeah re-installing it might be your best bet.

---

### Post by Mustard on 2006-02-07
I don't know whether this has been mentioned yet, but since your sudo is mucked up by the misconfigured hosts file, you will need to choose 'recovery mode' from the boot prompt, which will take you to a 'root prompt'.  As root you can edit the /etc/hosts file.  Below is a  copy and paste of the instructions I used for someone else with this problem.

> To edit the /etc/hosts file, you would need to get to a root prompt (as your sudo command will not be working with a misconfigured hosts file). The easiest way to do this is to use the recovery mode option from the grub menu at bootup.

When you get to a root prompt, open up the /etc/hosts file with this command.

```
nano /etc/hosts 
```

The /etc/hosts file normally looks something like this...

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

What you need to do is to edit the first line so that it contains a hostname for your computer.  Mine is called 'slave' as you can see above.  You can choose any name you like.  The current hostname can be found by using the 'hostname' command. By default ubuntu uses the hostname 'ubuntu'.

The first line should look something like this if you were using the hostname, 'ubuntu' for example..

```
127.0.0.1       localhost.localdomain   localhost       ubuntu
```

An additional command you can look at with regards to hostnames is this command below.

```
hostname #returns the current hostname
hostname <hostname>  #sets the hostname according to the value entered for <hostname>
```

This may tell you what your current hostname is, even though your /etc/hosts is misconfigured.  I would be curious if it does, as I haven't had the option to try it yet with a misconfigured hosts file.

---

### Post by jpkotta on 2006-02-07
Just out of curiosity, boogieman, but how did you erase your hostname?  Were you trying to change it by editing /etc/hosts and accidentally save it without a valid hostname?  

There are several threads like this in the forums.  I think there should be a warning at the top of /etc/hosts, since it's hard to change the file again when there is no root password.

---

### Post by boogieman on 2006-02-08
I'm having problems getting my wireless adapter to work.  I went to System > Adminstration > Networking and clicked the tab in the middle.  It had my hostname in there...I thought I had entered it while troubleshooting the network problem.  I deleted the hostname and started having problems from there.  I now cannot run anything from System > Administration or from a terminal.

---

### Post by jpkotta on 2006-02-08
Yeah...that's a problem.  You should not be able to render your system (almost) un-admin-able by deleting the hostname there.  

I played around with this a bit.  I unset my hostname with network-admin.  I had problems, but sudo worked until after rebooting.  Then I tried this.  I put a script ```
#!/bin/sh

PATH=/bin

if [[ -z `hostname` ]] ; then
    hostname ubuntu
fi
```
in /etc/fix_hostname.  Then I put a link to it in /etc/rc2.d/ such that it was the first one and rebooted.  It didn't completely fix the system, but I could sudo again.  

I think there should be a script like this to prevent this problem.  You can't argue that people should know what they're doing when they change the hostname.  My non-geek friends think I'm weird for naming my computers, but it's almost a necessity in the Unix world (then again, they think I'm weird for running Linux).  I wouldn't have expected a null hostname to break sudo.  Clearly, the script would have to do more than the example above.

It's late.  I'll learn how to file a bug report tomorrow and submit it.

---

### Post by boogieman on 2006-02-08
Sweet!  I'm glad something good happened at my expense.  I sure am learning a lot.

I couldn't get anything to work so I reinstalled it, resized my partitions, and everything's running great now!  Except for this dang wireless problem...

---

### Post by jpkotta on 2006-02-08
[https://launchpad.net/distros/ubuntu/+source/rescue/+bug/19553/](https://launchpad.net/distros/ubuntu/+source/rescue/+bug/19553/)

I'm not sure if I should submit this separately.

---

### Post by boogieman on 2006-02-08
jpkotta, you are my friend.  Like I said, I'm learning and this is certainly part of the process.  This community is AWESOME!

I work in an internet department (customer service-type job...all day I have to talk to people that have forgotten their User ID/password for our site) and the help all of the people in here provide is top notch and definitely worth paying for.

---

### Post by jpkotta on 2006-02-10
Part of why Linux is superior is the community.  I want people to use Linux, and helping solve problems keeps users.

I really dislike the Microsoft philosophy, but as a platform, Windows isn't that bad.  In many ways it's better than Linux.  But the nature of Linux is such that *if* it was given a chance (manufacturers put it on new computers, hardware vendors released drivers, more software was written for it (stuff that can't really be open-sourced)), then it would be ridiculously better than Windows.  The only way that's going to happen is with more users.

---

