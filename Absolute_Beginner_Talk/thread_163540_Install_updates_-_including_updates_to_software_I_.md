---
title: "Install updates - including updates to software I do not have?"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by stig on 2006-04-21
I am trying to figure out whether I should simply install all the updates that Ubuntu offers me at intervals or make selections. I did a search on the Forum and found the following thread which seems to suggest always installing all updates:

[http://www.ubuntuforums.org/showthread.php?t=139121&highlight=install+updates](http://www.ubuntuforums.org/showthread.php?t=139121&highlight=install+updates)

but it does not really answer my questions.

I would always install updates to the OS itself, of course. But I am less clear about applications. Obviously I would install OpenOffice updates because I have that installed. But today it offered, for example, an update to ClamAV which I do not have installed.

If I follow the suggestion in the thread the ClamAV update would be installed even though I don't have the software. Would this result in my computer eventually being littered with bits of unneccessary software? Or is the Updater actually more clever than I think and only install the appropriate updates for my selection of software?

Thanks for reading my questions!

---

### Post by Sef on 2006-04-21
I would uncheck anything you don't want to be on your system.   Otherwise it will put it on.

---

### Post by stig on 2006-04-21
[QUOTE=Sef]I would uncheck anything you don't want to be on your system.   Otherwise it will put it on.[/QUOTE]

For a newbie this is a bit difficult. Some things may be obvious, like the ClamAV, but in many cases I've never heard of the application. I guess there is no way of having the Updater check against the installed software and only install what is appropriate?

Would that be an improvement for Ubuntu in the future perhaps? (Make good thing even better!)

---

### Post by soc on 2006-04-21
:confused: :rolleyes: 

apt-get only updates what is already installed on your system, nothing else.

regarding clamav, you should make sure that it isn't already installed and no other piece of software depends on it.

but you should always install all available updates. it doesn't make sense if you don't update an installed application because you don't recognize the name. everything apt-get wants to update _is_ already installed on your system.
so maybe you should just install everything _with_ clamav so your system is up-to-date and then uninstall clamav afterwards so you might see what caused it to be installed.

---

### Post by stig on 2006-04-21
SOC, are you and Sef talking about the same thing - because if so then the advice is contradictory. I'm referring to the pop-up Updater which tells me there are updates available. You mention apt-get - is this Updater doing exactly the same as apt-get?
Thanks!

---

### Post by Mustard on 2006-04-21
The pop up updater only updates installed software.  The logical implication is the you have clamav installed.  You just didn't know, or forgot, you had it installed

---

### Post by macdo on 2006-04-21
AFAIK, the updater is indeed an apt-get front-end.

---

### Post by soc on 2006-04-24
if we talk about apt-get, synaptic, smart, update-manager, aptitude, app-install it means the same, the purpose of these applications is to update, install and uninstall software. just the way it is done is different. commandline, differnet guis, ...

---

### Post by stig on 2006-04-25
[QUOTE=Mustard]The pop up updater only updates installed software.  The logical implication is the you have clamav installed.  You just didn't know, or forgot, you had it installed[/QUOTE]

That's interesting because Synaptic shows no Clamav packages marked as installed. I don't know the command to run clamav but I have tried clamav and ClamAV in the terminal and it says "bash clamav command not known" or something similar.

I installed ClamAV a week or two ago and completely uninstalled it after a couple of days, both using Synaptic. So I guess there is a file left behind that Synaptic/apt-get recognises as ClamAV.

Everyone is saying that Synaptic/apt-get only updates installed software. To be more precise, does that mean that the updater only *shows* updates for installed software, or that it shows all updates but only *executes* updates for installed software. (I'm an editor by profession and that makes me pedantic!)

Thanks for all the help and discussion.

---

### Post by steve.horsley on 2006-04-25
Being pedantic, it only **shows** updates available for installed software. Something clearly thinks that clamav is still installed. You might try installing it and then de-installing it again.

---

