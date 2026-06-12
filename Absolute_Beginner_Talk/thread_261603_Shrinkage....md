---
title: "Shrinkage..."
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by dawhistler69 on 2006-09-20
I noticed that when I shrink certain screens down (minimize) I cannt call them back up.  Is there a setting to place all shrunk down windows on the botton tool bar or at least a command that would tell me all running applications?

Thanks in advance

mas

---

### Post by Arisna on 2006-09-20
It sounds to me like you might have windows open on different desktops.  Do you have a little pager applet at the bottom right of your display?  It should look like four gray boxes, one of them highlighted to show that you are using it.  You can click the different boxes to change desktops, where you will be able to access the open windows at each.

I believe you can configure your panel to show windows from all desktops by right-clicking the taskbar (middle of the bottom tool bar), going to preferences, and hunting around a bit.  I'd post more exact directions, but I'm not on GNOME right now.

Also, you can get a window list that will display all windows from all desktops by right clicking the panel, choosing Add to Panel, and choosing a Window List/Window Selector applet (not sure on the name).

I'll log into GNOME and check real quick if you need further assistance. :)

---

### Post by dawhistler69 on 2006-09-20
I have found that Synaptic is running in the background and I cannt call it up to stop it.  I do have 4 work spaces and have checked all of them for programs that are obviously running...to no avail

mas

---

### Post by bodhi.zazen on 2006-09-20
LOL :lol: I thought this was a thread on something else....

Was going to advise Viagra.

To kill an application:

In a terminal either:```
killall <application_name>
```

Or:```
ps -ax | grep <application_name>
kill <PID>
```
The ap-ax | grep <name> will give you the PID (Process ID) as you must kill by number, not name.

---

### Post by dawhistler69 on 2006-09-20
I wondered if anyone would get it...:o 
I think its a george castanza phrase.
Thanks for the help...I will attempt...will report back

---

### Post by dawhistler69 on 2006-09-20
it keeps saying that I can have only one process running at one time...
I have restarted the computer and went to all 4 workspaces to try to find where its running.  Just tried your suggestions and system did not recognize synaptic as correct...what about killing all apps, shutting down and starting  new session without saving exsisting settings?
also interesting handle you have...sorta like wiccan star with a zen name...cool

---

### Post by bodhi.zazen on 2006-09-20
Thanks.

Try with sudo.

Perhaps if you psted the error message I could be more helpful.

---

### Post by dawhistler69 on 2006-09-20
Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.

This comes up when I try to run updates from the top toolbar.

---

### Post by bodhi.zazen on 2006-09-20
> **dawhistler69 said:**
> Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first.

This comes up when I try to run updates from the top toolbar.

Try ```
ps -ax | grep aptitude
ps -ax | grep synaptic
```To get PID (the number).

sudo Kill <PID>

The | is on top of the \ key on the left. This is called a pipe.

---

### Post by dawhistler69 on 2006-09-20
I get the below message...

mas@mas-desktop:~$ ps -ax | grep aptitude
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
19550 pts/0    R+     0:00 grep aptitude
mas@mas-desktop:~$ ps -ax | grep synaptic
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
19572 pts/0    R+     0:00 grep synaptic
mas@mas-desktop:~$


when I try sudo I get command not found

sorry about this! appreciate all your help

---

### Post by fontenot_1031 on 2006-09-20
lol, shrinkage

---

### Post by dawhistler69 on 2006-09-20
Sorry to do this on such an esteemed forum...but,

in windoz ,  you can ctrl-alt-del and get a list of running programs and system processes.  From there you can merely highlight the one of your choosing and close it or kill it...anything like that on Ubuntu?

If not then I may have a hobbie for a while trying to create one.  :o)
mas

---

### Post by bodhi.zazen on 2006-09-20
> **dawhistler69 said:**
> Sorry to do this on such an esteemed forum...but,

in windoz ,  you can ctrl-alt-del and get a list of running programs and system processes.  From there you can merely highlight the one of your choosing and close it or kill it...anything like that on Ubuntu?

If not then I may have a hobbie for a while trying to create one.  :o)
mas

```
top
```

or ```
ps -x
```without the | grep <command>

What happens when you update via synaptic?

---

### Post by bodhi.zazen on 2006-09-20
Delete the lock file```
sudo rm /var/lib/apt/lists/lock
```

And re-try update.

---

### Post by dawhistler69 on 2006-09-21
Morning bodhi.zazen
I found a similar problem reported in June of 05...I did not save the message info tho...
It said that my symptoms were probably due to an interruption of an update and it gave several steps to correct it...and it worked.  I appreciate your follow up.
Thanks again

mas

---

### Post by dawhistler69 on 2006-09-21
Found it...
[http://ubuntuforums.org/showthread.php?t=87582&highlight=quit+close+force+processes](http://ubuntuforums.org/showthread.php?t=87582&highlight=quit+close+force+processes)

this is the thread that fixed the issue..

later

---

