---
title: "Bash?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by SuperPetRalf on 2007-03-02
Ok, im new to linux, I've been talking to one of my mentors who got me into this, so far im liking the ability to tweak just abotu anythink, but its a little overwelming.

Anywho, I herd about about making scripts, looked at a few websites and i know abit about programming (Visual basic(OK I Accept it's not a REAL language)).

Anyway I get the concept but dont know how to create these scripts what do i write them in and how do i run them, if anones got anytime to give me the basics I'd appreciate it.
At the moment im running on the assumption that they are create din sumthink like note pad but what then?

SuperPetRalf. Cheers.

---

### Post by kidders on 2007-03-02
Hi there,

Bash is a shell (one of many). A Bash *script* is little more than a sequence of commands to be processed by it, much as a DOS shell script works.

To have Bash process a shell script, preface it with **#!/bin/bash** ... it doesn't matter what you created it with. Equally, you could use other shells (like zsh, which is another popular choice) ... or even something like PHP.

---

### Post by william_hunter on 2007-03-03
This fits in with a problem I am having as well..could someone help me understand how to make this script do what it is supposed to, which is to fire up a game watchdog process called nwnx2?

> 
while [ nwncheck != 1 ]
do
sleep 10
export LD_PRELOAD=./nwnx2.so
./nwserver -module "modulname"
unset
unset LD_PRELOAD
done 


Here is the current nwnstartup.sh script I am using, which starts the game server up just fine, but it does not seem to start the nwnx2 process that is supposed to reboot the server in event of a crash:

> 
#!/bin/sh

export LD_PRELOAD=./nwnx2.so


./nwserver -module "Tharagon02062007" -dmpassword diecheater -maxclients 40 -minlevel 1 -maxlevel 40  -difficulty 4 -publicserver 1 -elc 0 -ilr 0 -port 5121 -gametype 3


I am no genius, and this is something relatively new to me. Any help would be appreciated. Please ask if you think I need to clarify.

---

### Post by kidders on 2007-03-03
Hi there,

The second script you posted seems to start up a game server. The first one looks like it does more or less the same thing, except that it does it every 10 seconds, unless/until something called "nwncheck" returns exit code 1, in which case it simply finishes.

I don't see a reference to nwnx2. :confused: Have you posted the right things?

(For SuperPetRalf's benefit, these scripts are written for **sh**, not **bash** ... but there isn't really a huge difference.)

---

### Post by william_hunter on 2007-03-03
See thats what has me confused. NWNX2 is in the first few lines of the script, and there seems to be a variable being called (nwncheck) that isnt defined. NWNX2 is basically a wrapper that adds scripting functionality and some databasing to the game, while also being able to restart the nwserver process if it crashes. I cant see how to integrate these two things. I suppose I should try harder to hunt down the guy that wrote that first script. 

Oh, and these are essentialy the same script. The first one was sent to me when I asked for help on the nwnx forums. 

The thing I dont get is the "how" of shell scripting. 

I should have been more clear when I posted initially. Here is what I want to know, now that I am thinking straight:  Can I re-write the second script to work in a timed loop like that first one does?

---

### Post by kidders on 2007-03-04
> **william_hunter said:**
> Can I re-write the second script to work in a timed loop like that first one does?Yes, of course. What would you like it to do, exactly?

---

### Post by william_hunter on 2007-03-04
Well, I have to use the shell script to start the server instance. I would like the script to continue to run in the background after the server is started, and check every so often to make sure it is. If it is not, restart it. Thats what the "./nwserver -module name" call does, fire up the server. 

this is the current shell script I use to start the server, and it works nicely but does not restart in event of a server crash or other shutdown:

> 
#!/bin/sh

export LD_PRELOAD=./nwnx2.so


./nwserver -module "Tharagon02062007" -dmpassword diecheater -maxclients 40 -minlevel 1 -maxlevel 40 -difficulty 4 -publicserver 1 -elc 0 -ilr 0 -port 5121 -gametype 3



I need to keep the nwnx2.so reference because that is a function wrapper that I use to run plugins. The commands after the module name are basically instructions for the server app and what/where to post the game on gamespy.

Thanks for your help, by the way. I feel like a little kid asking a teacher for help, but I am stumped.

---

### Post by kidders on 2007-03-04
> **william_hunter said:**
> I feel like a little kid asking a teacher for help, but I am stumped.Hehe!

See what you think of something like this...

```
#!/bin/bash

ENV="LD_PRELOAD=/lib/nwnx2.so"
CMD="/usr/local/bin/nwserver"
ARG="-minlevel 1 -maxlevel 40"

if [ -n "`pidof -x $CMD`" ]; then
	echo "Game server already running"
	exit 1
fi

PID=9999999
while [ 1 ]; do

	if [ -z "`ps hp $PID`" ]; then
		echo "Restarting game server"

		# Try to start the server
		export ${ENV}; ${CMD} ${ARG}&
		PID=$!

		# Give the server a chance to get started
		sleep 5

		if [ -z "`ps hp $PID`" ]; then
			echo "Server stayed up for less than 5 seconds. Aborted."
			exit 2
		fi
	fi

	sleep 90

done
```

This is just thrown together (and I'm no expert), so it's far from perfect, but essentially...

[LIST]
[*]My script first tries to find an existing server process, in case it somehow manages to get called more than once.
[*]It checks for the need to restart the server every 90 seconds.
[*]If something goes badly wrong, and the server shuts down immediately every time it's relaunched, the script terminates, to avoid an infinite loop of failures.
[/LIST]

Would something like that suit your purposes?

---

### Post by william_hunter on 2007-03-04
I'll give that a shot and see what happens. I am assuming the ARG is where I put the commands in the script I posted for server parameters?

---

### Post by maddog39 on 2007-03-04
I would highly recommend you read everything on this website:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

It will teach you almost everything that Bash can do. With tons of examples and activity type things. That should help you alot.

---

### Post by kidders on 2007-03-04
> **maddog39 said:**
> I would highly recommend you read everything on this website:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)Yep! My sample script is just a suggestion to get you started ... I wouldn't suggest actually executing it until you are confident you can follow it, and fix any mistakes I made!

(That's a nice link btw, maddog39 ... I'll have to remember it!)

---

### Post by william_hunter on 2007-03-05
Thanks folks. I have not yet had time to test that script, but i will give it a shot today.I am also pleased to find a resource to read through.

---

### Post by jonbob on 2007-03-05
I have another question...

i wont run ssh in a script. It should connest to an other host and run there mount.

thanks for help

jonbob

---

### Post by kidders on 2007-03-05
If I understand you correctly, you want to run a single command on a remote host over SSH. Shell scripting is not required ... check out SSH's man page.

If you have questions about mounting filesystems or using SSH, please start your own thread ... the original poster probably won't appreciate another hijack!

---

