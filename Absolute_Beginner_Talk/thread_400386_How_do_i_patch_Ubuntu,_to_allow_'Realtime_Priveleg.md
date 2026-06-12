---
title: "How do i patch Ubuntu, to allow 'Realtime Priveleges' - Vanilla Kernel? Sounds tasty."
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by SATTI on 2007-04-03
Ok so after much clicking, coffee slurping, tears and swearing...i finally got my wireless working in Ubuntu 7.04:D I thought that it would be all down hill from there, but it seems i was tricked...!

     I have installed Ardour2, JACK and the control gui for Jack. Now i want run JACK in _realtime_ so that i may experience the wonders of low latency...but after reading a few posts and googling, it appears dint have the apparent Realtime Privileges. 

So, i used the Synaptic package manager to download and install the low-latency kernel (thinking that this would give me the appropriate permissions) 

Unfortunately, it didn't. 

SO, i hop into the IRC chat, and one of the lovely users in there advise me to download a vanilla kernel, and patch it with a LMS-low latency server patch. 'Great' I think.

SO away i go, google hopping like a madman...only to find it isn't that simple. It appears that i have to build a new kernel, and integrate it, then change the permissions. 

I just want to run Ardour, and JACK with realtime enabled. At the moment i'm getting loads of xruns, and it is using too much of my CPU. Running without realtime is not really an option.

Please somebody, save me from Linux! I'm almost there, i know it. It took me 3 days to get my wireless going, lots of coffee to get the printer installed (it still isn't printing, but at least the driver is installed)

Give me an edible vanilla kernel, I would be a happy Linux newbie:)

Thanks

Satti.

[-o<

---

### Post by christhemonkey on 2007-04-03
The -lowlatency kernel is already patched with the relevant mingo patches to allow realtime.

You might check whether your in the "audio" group (GID 29) and also what is the contents of /etc/security/limits.conf

It should look similar to this:
```
@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10
```

---

### Post by SATTI on 2007-04-03
Thank you for the fast reply; 

Please tell what the 'audio group GID-29' is.

This is the output of my limits.conf file;

# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to
#        - rtprio - max realtime priority
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#@student        -       maxlogins       4

# End of file

---

### Post by christhemonkey on 2007-04-03
All the lines in that file are commented out, so you wont be able to get realtime privileges, you need to add these lines into that file (id put them just before "# End of file")

> @audio - rtprio 99
@audio - memlock 250000
@audio - nice -10

Go into users and groups on system > Administration > Users and groups (or whatever its called, not in front of an ubuntu box atm so cant remember!)

Then check if your user is in group called audio (whos unique id number is 29)

---

### Post by SATTI on 2007-04-03
Ok i removed the # from the file;

# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
<domain>        <type>  <item>  <value>

Where:
<domain> can be:
        - an user name
        - a group name, with @group syntax
        - the wildcard *, for default entry
        - the wildcard %, can be also used with %group syntax,
                 for maxlogin limit

<type> can have the two values:
        - "soft" for enforcing the soft limits
        - "hard" for enforcing hard limits

<item> can be one of the following:
        - core - limits the core file size (KB)
        - data - max data size (KB)
        - fsize - maximum filesize (KB)
        - memlock - max locked-in-memory address space (KB)
        - nofile - max number of open files
        - rss - max resident set size (KB)
        - stack - max stack size (KB)
        - cpu - max CPU time (MIN)
        - nproc - max number of processes
        - as - address space limit
        - maxlogins - max number of logins for this user
        - maxsyslogins - max number of logins on the system
        - priority - the priority to run user process with
        - locks - max number of file locks the user can hold
        - sigpending - max number of pending signals
        - msgqueue - max memory used by POSIX message queues (bytes)
        - nice - max nice priority allowed to raise to
        - rtprio - max realtime priority

<domain>      <type>  <item>         <value>


*               soft    core            0
*               hard    rss             10000
@student        hard    nproc           20
@faculty        soft    nproc           20
@faculty        hard    nproc           50
ftp             hard    nproc           0
@student        -       maxlogins       4

@audio - rtprio 99
@audio - memlock 250000
@audio - nice -10

# End of file


When i go into user and groups; I don't see on called Audio with id 29.

My user group is home, with id 1000

---

### Post by christhemonkey on 2007-04-03
I didnt mean umcomment every line!
That would lead to a very very confused computer :D

Give me a minute whilst i go look on my ubuntu pc, cant remember where it is, i just know you have to be in the group audio (hence the @audio in the limits.conf)

---

### Post by SATTI on 2007-04-03
Ok, got it!

I fixed the file so it is as it was before....:)

I added those lines to the bottom, as you explained. I'm still searching for that user group.

---

### Post by christhemonkey on 2007-04-03
Ok on ubuntu edgy i had to create the audio group (by clicking manage groups) and give it a Group ID of 29 and add me as the only member.

Try doing that?

---

### Post by SATTI on 2007-04-03
That doesn't seem to work;

I click 'manage groups' then 'add group' then type 'audio' as the group name '29' as the id. and select 'Stephen' as the user (there are only two, Stephen and root)

But there is no new audio group in the list; if goto properties of the user 'Stephen' there is no audio option in the list.

---

### Post by christhemonkey on 2007-04-03
Try adding the group via command line:
```
sudo groupadd -g 29 audio
sudo gpasswd -a stephen audio 
```

---

### Post by SATTI on 2007-04-03
Ok; i've typed that.

No errors, so it must of worked. I tried typing it again to make sure, and the terminal reported that the group audio was already added. 

But still, when i load JACK and enable the 'realtime' option, the program still fails with the error 'could not connect JACK to server as client' This does not happen when the realtime option is unselected, so I know for sure there is a problem here.

I want to thank you for the help so far, i wouldn't have been able to get this far with out your fast response.

Kudos.

---

### Post by christhemonkey on 2007-04-03
Try running jack from the command line like this:
```
jackd -R -d alsa 
```
And paste the output here.

Im going to the pub now, so i cant check this thread again till tomorrow.
Hope someone else helps till then!

---

### Post by SATTI on 2007-04-03
Thank you so much for all of your help Chris, you gave me a good push in the right direction. Eventually what i did was, uninstall JACK, and reinstalled it to a different library. As it was installed under Local. I then replaced the ALSA driver, and played around with the settings in rtlimits and qjackclt .config files.

At 12:30 I finally got RT working in JACK! And Ardour2 runs soooo well now.

Thank you again, and applause for the folks in #lad on freenode.irc they really helped me out too.

Case closed!

Stephen/

---

### Post by christhemonkey on 2007-04-04
Congratulations, im glad you got it sorted!

---

