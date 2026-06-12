---
title: "Insallation Problem"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by Seeds on 2005-08-04
Hello I am trying to switch from Windows to Ubuntu, but it just won't install! The first part of the installation seems to work nicely, then it ejects the CD and restarts to finish its installation. The second screen starts up and it looks like it's going along fine, but after a few good minutes it freezes! I thought it had to do with either power management or something to do with "Generating Locales" as it froze at that screen when I tried to install it twice, so I took some extra precautions for the third installation. I turned off some settings in power management, so it wouldn't power down or shut down on it's own for any reason, and then I ran the installer again, this time with "noapic nolapic" and loe and behold, it froze again! Even at an earlier spot this time. This time it froze somewhere saying, "depackaging office" or something like that. I need some help  :-| .

---

### Post by poofyhairguy on 2005-08-04
[QUOTE=Seeds]Hello I am trying to switch from Windows to Ubuntu, but it just won't install! The first part of the installation seems to work nicely, then it ejects the CD and restarts to finish its installation. The second screen starts up and it looks like it's going along fine, but after a few good minutes it freezes! I thought it had to do with either power management or something to do with "Generating Locales" as it froze at that screen when I tried to install it twice, so I took some extra precautions for the third installation. I turned off some settings in power management, so it wouldn't power down or shut down on it's own for any reason, and then I ran the installer again, this time with "noapic nolapic" and loe and behold, it froze again! Even at an earlier spot this time. This time it froze somewhere saying, "depackaging office" or something like that. I need some help  :-| .[/QUOTE]

What do you have now? Can you boot to the commandline? Do you have broadband? cause here is what I would do if I was you:

use this command:

> sudo pico /etc/apt/sources.list

Manually edit the file to look like this one:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Be SURE to delete the first line concerning the CD. That is your problem, a bunk install CD.

(you would wan to do this eventually anyway). When you are done, hot the ctrl key and the "x" key at the same time. Tell it yes when it askes to save the file and exit.

Then type this command

> sudo apt-get update

then when its done:

> sudo apt-get install ubuntu-desktop

You could also:

1. Burn a new install CD a try again.

2. Do the server install (type server on the first screen of the install CD before hitting enter) then following my directions.

I have done what I said to do before, adn it worked for me.

---

### Post by Seeds on 2005-08-04
[QUOTE=poofyhairguy]What do you have now? Can you boot to the commandline? Do you have broadband? cause here is what I would do if I was you:

use this command:



Manually edit the file to look like this one:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Be SURE to delete the first line concerning the CD. That is your problem, a bunk install CD.

(you would wan to do this eventually anyway). When you are done, hot the ctrl key and the "x" key at the same time. Tell it yes when it askes to save the file and exit.

Then type this command



then when its done:



You could also:

1. Burn a new install CD a try again.

2. Do the server install (type server on the first screen of the install CD before hitting enter) then following my directions.

I have done what I said to do before, adn it worked for me.[/QUOTE]
 Right now I can boot the ubuntu but what happens is that it looks like it's loading with the circle mouse thing and a black screen, the all of a sudden my monitor just falls asleep and stays there. When I press the power button and error message comes on saying it didn't install all the packages and it shuts down. Now I went into the system-restore (or w/e it is) boot option and I get a command line, just for kicks I typed in "exec install" and then the mouse loading thing come up, then for a breif second I actually saw the menu in all it's glory! Then it fell asleep again. During the installation it was mentioned several times that my processor is known not to support power saving, maybe that's a problem, is there a way to disable it? Can I do what you said from system restore thing (not sure what it's called again)?

---

### Post by Seeds on 2005-08-04
Ok so I did everything you said, but Ubuntu said "You have the latest version". So i went and tried sudo apt-get upgrade Ubuntu-desktop, and it upgraded a bunch of things. Problem is I went and tried to boot into Ubuntu desktop again and again I saw the login screen for a few seconds, and then my monitor fell asleep! Is there a way to fix this problem?

---

