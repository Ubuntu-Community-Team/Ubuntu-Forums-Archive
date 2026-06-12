---
title: "sorting out apt-get"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Kevincol on 2006-01-08
Hi ive just installed 5.10 no problems at all,it figured out all my hardware and i must say im impressed so far.a couple of of small things though 1. im trying to open some publisher files which it wont recognise and 2. i mucked up a download in add applications and now it tells me apt-get or apptitude is still running, how do i stop these applications? Kevin

---

### Post by Mustard on 2006-01-08
Can you describe how you 'mucked up' the install of the application, so I am sure I know whats going on?

Secondly, can you describe the exact error message you receive when you attempt to use it again?

The yelp update application will occassionally be running in the background using apt-get ( I think), so I wouldn't want to kill the process while it was working.

In your Applications>>System Tools menu you will find a System Monitor which will show all the processes that are running.  Right clicking on a process will give you the option of ending or killing a process.  I would just be careful with what you kill and that you have given the system enough time to actually finish whatever process it might be in the middle of doing.

Its quite possible that 'Add Applications' has locked other applications from installing due to something you have done during the installation process, I'd just like to be certain. :)

---

### Post by poofyhairguy on 2006-01-08
[QUOTE=Kevincol] im trying to open some publisher files which it wont recognise [/QUOTE]

I used my superpowers to try to help you with the publisher thing....this Google cache of a former wikipedia entry is the best answer you are going to find:

[http://72.14.203.104/search?q=cache:IPqtUNhnTycJ:en.wikipedia.org/wiki/MS_publisher+microsoft+publisher+linux&hl=en&client=firefox-a](http://72.14.203.104/search?q=cache:IPqtUNhnTycJ:en.wikipedia.org/wiki/MS_publisher+microsoft+publisher+linux&hl=en&client=firefox-a)

---

### Post by Kevincol on 2006-01-08
Hi Mustard thanks for getting back to me so quick.
In the system monitor only the only the Gnome system moniter is running.
In add applications i get an error message (unable to get exclusive lock which means apt-get or aptitude are already running please close them.)
And the synaptic package manager tells me E;dpkg was interupted you must manually run 'dpkg--configure-a'to correct the problem.
I tried this in the terminal but ut told me it was an incorrect command.
!/2 way through a down load my computer froze and i was forced to reboot.
Thanks Kevin

---

### Post by Mustard on 2006-01-08
> **Kevincol]Hi Mustard thanks for getting back to me so quick.
In the system monitor only the only the Gnome system moniter is running.
In add applications i get an error message (unable to get exclusive lock which means apt-get or aptitude are already running please close them.)
And the synaptic package manager tells me E said:**
> 

You probably need to put a 'sudo' command in front of that command above...

Like this (I'm just copying the command you put above to, so double check I got it right)

```
sudo dpkg --configure -a 
#(or whatever it says to do.  The important thing is you use 'sudo' in front.
```

My guess is that there is a lock file in your /var directory now that is locking the program until this situation is fixed.

Looking at the manual for dpkg, this is what it does...

[quote=dpkg manual]dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package.  If -a or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

              Configuring consists of the following steps:

              1. Unpack the configuration files, and at the same time back  up
              the  old  configuration  files,  so that they can be restored if
              something goes wrong.

              2. Run postinst script, if provided by the package.


---

