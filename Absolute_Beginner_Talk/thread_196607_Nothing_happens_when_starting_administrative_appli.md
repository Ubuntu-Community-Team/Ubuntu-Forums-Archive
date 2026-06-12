---
title: "Nothing happens when starting administrative application"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by nilsh on 2006-06-14
Hello!

I have used ubuntu for a week now, very satisfied. But suddenly today, It seems like I can't access any administrative programs. I was trying to get into synaptic and login window today, but the only one happening is "starting administrative application" on the status bar, then it disappear after 20 seconds or so.

So, what is wrong here?

---

### Post by givré on 2006-06-14
Try to launch one of them via the terminal to know what is wrong.
For exemple:
```
sudo synaptic
```
or for the graphical version (recommended for graphical apps)
```
gksu synaptic
```

---

### Post by nilsh on 2006-06-15
Hmm, I get this error:

sudo: unable to lookup lynx (my computer) via gethostbyname()

I cant enter my password or anything.

---

### Post by stupidkid on 2006-06-15
Did you edit any of your hostname files (e.g. /etc/hostname)? I've done that before and it wouldn't let me start root applications.

---

### Post by taurus on 2006-06-15
Have you changed anything in /etc/hosts lately?

---

### Post by nilsh on 2006-06-15
Hmm, yes I have. My computer's name was "nilsh" before, but I wanted to change it. So I edited the hostname file from nilsh to lynx. Should I change it back?

edit:

Ok, I tried to change it back to nilsh, but of course, it wont let me do it. Hmm, I really dont know how to edit that file now. It just gives that gethostname error...

---

### Post by taurus on 2006-06-15
And what does your /etc/hosts look like now?  The name in /etc/hostname should match the name in /etc/hosts...

---

### Post by stupidkid on 2006-06-16
Uh...how does it not let you? /etc/hostname is just a normal file. Can you post the error you get when you try to change it?

And if you want to change your hostname, go to System -> Administration -> Networking and you can change it there.

---

### Post by nilsh on 2006-06-16
My hosts looks like this :

127.0.0.1 localhost nilsh
127.0.1.1 nilsh

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

and my hostname is now lynx.

Problem is, I can't change anything, since the error appearing then is:

sudo: unable to lookup lynx via gethostbyname()

---

### Post by stupidkid on 2006-06-17
Yea edit /etc/hostname and change the name back to nilsh. Now reboot (I think you have to do this) and go to System -> Admin -> Networking and change your hostname there.

---

### Post by tedrampart on 2006-07-15
> **stupidkid said:**
> Yea edit /etc/hostname and change the name back to nilsh. Now reboot (I think you have to do this) and go to System -> Admin -> Networking and change your hostname there.

hey.. sorry, I know this is an old post, but I just encountered this problem today.  I'm (re)trying linux, the first time since my old slackware on a 486 about 6 years ago.

my problem seems to be the same, only there's no way I can edit the hostname (its read-only), and anytime I try loading "networking" under the system/preferences menu, it comes up with the old "starting administrative....".  

is there anyway of fixing this beyond whats already been said?  I can't switch to root in any way shape or form, because it deny's my password which worked earlier today (before this happened).  I've searched the forum high and low, and found nothing to resolve this.  

oh yea, and also the /etc/hostname file appears to be empty, and it won't let me edit it and save.  

much help is needed, I'm about ready to throw my laptop out the window.

---

### Post by loksipan on 2006-11-24
Hi nlish

I feel your pain - I had TWO(!) machines go down with the same problem.  

The following worked for me

Boot-up
Change Session type to Failsafe and login - you'll get a terminal window

>sudo passwd root
password>    type your password here
Enter New UNIX password>  ditto
confirm password> ditto
root> nano /etc/hostname

You will now get a terminal text editor open with a blank page, type:-

127.0.0.1 localhost

Use CTRL-O to write the file and CTRL-X to exit
type exit to exit root
type exit to exit the terminal 
and shutdown from the login screen
Reboot
Change Session type back to KDE or Gnome
login again
You should now be able to access admin programs.
You'll find the hostname in SYSTEM->NETWORKING->General TAB has changed to 
127.0.0.1 localhost

---

### Post by BadDolphin on 2006-12-13
I'm a relative newbie, but I also made the dire mistake of thinking that I could actually use /etc/hosts to prevent certain annoying domains from resolving... like on every other computer I've used in recent years.  I can hardly believe that there's no warning during install, or splashed in bold uppercase letters "DO NOT EDIT /etc/hosts or you will damage your system" as the opening sentence of the Ubuntu FAQ.

Months later I'm still fighting with problems that resulted from it (no, enabling the root account and using it to change the pc's hostname did nothing at all to help).  I would be thrilled if someone corrects me in a followup post, but the only solution that actually works is to reinstall the OS all over again.

Here's why I'm so frustrated...

When I try to get updates, it goes to "starting Administrative Application" but it never opens.  The same with other programs, sometimes even Firefox, but that happens randomly and a reboot fixes that.

user@closetbox:~$ sudo synaptic
sudo: unable to lookup closetbox via gethostbyname()
user@closetbox:~$ gksu synaptic
sudo: unable to lookup closetbox via gethostbyname()

user@closetbox:~$ cat /etc/hostname 
closetbox
user@closetbox:~$ cat /etc/hosts
127.0.0.1       localhost

When I try to open System -> Admin -> Networking, it says "Starting Networking" but it also just never opens.

FOLLOWING INSTRUCTIONS IN ABOVE POST ALSO DOES NOT HELP:

As described above, I rebooted into "recovery mode" (I saw nothing called "failsafe").

I typed "sudo passwd root" and got the usual "unable to lookup up by gethostname" but the prompt did show me as root, at least.  So I edited the /etc/hostname file as described above,removing the actual hostname, changing it so that the contents read "127.0.0.1 localhost"

I saved it, exited, rebooted, and have precisely the same problem- I can't get any system updates, and it continues to hang on "starting Administrative Application" before closing/vanishing yet again.

I've tried other things, like simply changing the hostname to read a single hostname word, like "test" or something (no quotes).  In some posts I get the feeling that some people believe that /etc/hosts and /etc/hostname are one and the same.  But I'm still astonished that I could cause major problems that drag on for months over something that could have been easily avoided had there been an appropriate warning.

---

### Post by argie on 2006-12-13
Alright, follow the same procedure and change ```
127.0.0.1 localhost
```
to ```
127.0.0.1 localhost closetbox
```

That's in /etc/hosts.

---

### Post by BadDolphin on 2006-12-13
Still no joy.

[I]closetbox:~$ cat /etc/hosts
127.0.0.1       localhost       closetbox
user@closetbox:~$ cat /etc/hostname
closetbox
user@closetbox:~$ gksu synaptic
sudo: unable to lookup
closetbox via gethostbyname()[/I]

One other thing I've noticed, though this may not be related... when browsing, no DNS is cached at all locally- I could type "google.com" in a browser window, and it will sit on "looking up google.com" for a while. It does this with every use of the browser, even sites I go to all the time.  It does seem to cache it for a few seconds, but maybe even ten seconds.  Though it doesn't seem related, it's exceptionally odd.

**UPDATE A FEW DAYS LATER** (Saturday the 16th):
I'm still unable to get this working, there MUST be something other than /etc/hosts and /etc/hostname that affects how this works.  Does anyone know of a way to just totally defeat or circumvent this whole "gethostbyname()" thing?  Can I run the whole GNOME desktop as root?  

Not sure if this will help anyone, but here's another set of configs that DO NOT WORK:
# hostname
closetbox
# cat /etc/hostname
closetbox
# cat /etc/hosts
127.0.0.1       localhost
127.0.0.1       closetbox

---

