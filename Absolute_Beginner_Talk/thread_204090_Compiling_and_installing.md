---
title: "Compiling and installing"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Justgeek on 2006-06-26
Hi.,

Ive been reading the guides on the ubuntu and didn't get anywhere.

1. Downloaded a Danguardian.tar.gz
2. Read that I had to compile it so I had a .deb. 
3. Tried installing the build-essential as stated. 
4. Couldn't find the program after installing.
5. Got mad and left the keyboard.

I really need this software running on the Ubuntu. There is packages for redhat etc but not ubuntu

---

### Post by Kimm on 2006-06-26
What is the program?
Perhaps someone here can build a package for you.

Tip: Open a terminal and try typing the name of the program (with small letters) and press Enter.

---

### Post by Justgeek on 2006-06-26
Okay got the program installed. Used a rpm and Alien software that made it into a .deb.

But where did it install it, how can I use the program.

The program is: DansGuardian 2.8.0

---

### Post by Brunellus on 2006-06-26
there's ZERO reason to compile and install dansguardian;  it's already in the universe repository.

enable the 'universe' and 'multiverse' repositories in synaptic, refresh, search for the package, and install that way.  

As to actually running it:  a quick look at the homepage for the program shows a link to documentation and howtos, including a detailed howto on getting it up and running on a single host running Ubuntu:

[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php)


The truth is out there.

---

### Post by Kimm on 2006-06-26
Ehem... if you didnt notice... this program is in the repositories...

sudo apt-get install dansguardian

---

### Post by Justgeek on 2006-06-26
hmm tried looking there, without luck at first...

Got it installed, but really cant figure out the software. Shouldn't their be an grafic interface ?

So lost in this Linux world

---

### Post by Brunellus on 2006-06-26
[QUOTE=Justgeek]hmm tried looking there, without luck at first...

Got it installed, but really cant figure out the software. Shouldn't their be an grafic interface ?

So lost in this Linux world[/QUOTE]
no, there probably isn't a graphical interface.  there probably are detailed instructions on the website for dansguardian.  

Just so you know:  in linux and unix, the priorities are generally, in order 1) making it work, then 2) making it pretty.  Graphical interfaces are less important than functional software, for one, and for two, there are fewer devleopers who tend to specialize in GUI development anyway.

So most tools will ship without GUIs.  Not a big deal, since many such tools (like this filitering software) will be implemented at the server level.  Servers don't have monitors:  you connect to them remotely secure shells (yeah, text-based command lines!)

---

### Post by Justgeek on 2006-06-26
Oki. Just gotta stick with it then

Because the only thing I need Linux for is running a webbrowser that only should be able to run 1 site only.

Seems a little overkill to have a windows for that.

---

### Post by Brunellus on 2006-06-26
you could conceivably configure a firewall to block all packets that did not come from a specified set of hosts, thus limiting web browsing to only those hosts permitted by the firewall.  No further filtering necessary.

---

