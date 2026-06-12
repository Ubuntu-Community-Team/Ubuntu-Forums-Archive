---
title: "Synergy Questions"
date: 2005-08-30
forum: Absolute Beginner Talk
---

### Post by stumpadoodle on 2005-08-30
K so i have a windows box in my room and Ubuntu on my laptop...and I was wondering how I could get them to share one mouse and keyboard. I did some research out on the net for a while and decided that this Synergy thing was basically the way to go. There are only a few things I'm not sure I understand:

One of these things is the fact that you need a server to connect the computer through? Do you have to own the server and if so, how do i go about that? Also, how must the computers be connected? Is there a cable thing or is it just straight through whatever server you're connected to...

I need some step by step intructions on this one guys...cause I understand how to install the thing and al with Synaptic Package Manager but im not sure about the whole server part...im a total linux noob

---

### Post by xmastree on 2005-08-30
[QUOTE=stumpadoodle]and I was wondering how I could get them to share one mouse and keyboard.[/QUOTE]How about a [KVM switch](http://en.wikipedia.org/wiki/KVM_switch) ?

---

### Post by N'Jal on 2005-08-30
with a laptop? Is that possible?

---

### Post by xmastree on 2005-08-30
I'm assuming that stumpadoodle wants to use the keyboard and mouse from his desktop (Win) PC with his ubuntu laptop and the Win desktop. A simple $30 KVM ought to be able to to that assuming the laptop has connections for external ones.
Could do the monitor too if necessary.

---

### Post by stumpadoodle on 2005-08-30
yeah but i've already gotten synergy installed on both this laptop and the desktop, and i was just wondering about the whole server thing. Do you need to own your own server to link the computers through or is there like a free access one i could use?

Also, when using synergy, do the two computers have to be linked in anyway? (not KVM switch, im don't wanna pay for that....) or are all the signals simply routed through the server that you specify?

---

### Post by tospig on 2005-09-01
hi stumpadoodle,

i'm also a complete newbie to linux, but i think i know the answer to your question because i used to have synergy running on windows and linux. 

you set the server for synergy as one of the computers (ie, the windows one), and follow the instructions/set-up procedure. if you like, i can give you a real step by step guide on how to do this, but first there's one thing i ask - 

how do i download/install synergy for ubuntu? (told ya i was a noob) - a friend of mine did this for me last time and i have no idea what he did, and i'd like to know, and frankly this whole linux thing is really quite scary :o 

And yes the two computers do need to be linked across the same network.

---

### Post by iceshaft07 on 2005-09-02
to get synergy installed on Ubuntu, you need to install the extra repositories (directions for that lie at the ubuntuguide). its one of the first steps.

after that, everything will be in the synaptic package manager. look for it in there.

when you have it installed, start up synergy on the windows machine.

you want the windows machine to be the server. set up the screens as you like. you type in the name of the computer.

so, i have windows on one computer, name "Pooter"...my laptop is named "Minipooter".

so, add 2 computers, Pooter, and Minipooter.
select Pooter
Left : Minipooter (when the mouse is dragged to the left on pooter, it goes to minipooter)

select Minipooter
Right : Pooter (when the mouse is dragged on minipooter to the right, it goes to pooter)

then, click on start, then go to run
type command/cmd
type ipconfig and hit enter
write down the ip address then get on your ubuntu laptop

assuming synergy is installed...
click on applications then go to run

type "synergyc <ipaddress you wrote down earlier>" (no quotes, no < or >)

if everything works properly, the mouse will disappear on the laptop, and you can drag.

---

### Post by tospig on 2005-09-02
> to get synergy installed on Ubuntu, you need to install the extra repositories (directions for that lie at the ubuntuguide). its one of the first steps.

after that, everything will be in the synaptic package manager. look for it in there.

thanks iceshaft :)

i now have another question: how do you make it run after you log in? the synergy site suggests the files you need to alter, and it works for the log-on page, but not after that? the files it says you need to edit aren't there?

ok, i've just answered my own question: system > preferences > sessions > startup programs

yay :D

---

### Post by tospig on 2005-09-05
another question i have:

it's now not workign at all. my 2 computers can see each other on the network, but when i turn them on and run synergy nothing happens. i had it working for a day, then turned off the machines. the next day when i turned them back on it didn't work. i didn't change any settings or anything, any ideas as to why it's not working?

---

### Post by arz_thor on 2005-11-27
Hi everyone,

I am trying to run the synergy server on my Breezy (PPC) and I get this error reply when I try to specify a client address:

FATAL: synergys.cpp,383: failed to start server: cannot bind address: Cannot assign requested address
DEBUG: CScreen.cpp,49: closed display

The server seems to be working if I don't specify any address, but then synergy won't work at all...

Can anybody help me ?

Thx.

---

