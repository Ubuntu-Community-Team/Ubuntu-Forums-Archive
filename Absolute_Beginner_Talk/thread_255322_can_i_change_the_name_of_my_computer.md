---
title: "can i change the name of my computer?"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by mokmoki on 2006-09-11
hi to everyone, i'm a complete ubuntu newbie. i occassionally use Mandrake Linux in our school from time to time, just to type programs and compile them and stuff. in terms of customization and day-to-day use, i'm a complete linux newb.

i found the forums full of very useful info, (my very first task was to mount my other OS/drives, yahoo!) but i can't seem to find a topic for this...

back to the question, is it possible to change the name of your machine? the name you set while installing...

thanks for all the help!

---

### Post by monktbd on 2006-09-11
try

> sudo hostname mynewcompname

and of course set mynewcompname to whatever you would like.

edit: you might need to log out and back in again because i think that gnome uses the hostname quite a lot and things could be acting weird then.

---

### Post by risbac on 2006-09-11
Hi there, very useful:

[http://ubuntuguide.org/wiki/Ubuntu#How_to_change_computer_name](http://ubuntuguide.org/wiki/Ubuntu#How_to_change_computer_name)

---

### Post by steve.horsley on 2006-09-11
> **monktbd said:**
> try
> 
sudo hostname mynewcompname

and of course set mynewcompname to whatever you would like.

edit: you might need to log out and back in again because i think that gnome uses the hostname quite a lot and things could be acting weird then.

[SIZE="6"][COLOR="Red"]Nooooo!!![/COLOR][/SIZE]

This will leave him unable to use sudo to do any more administrative work. You **must** change the contents of /etc/hostname and /etc/hosts to match. You can either do this by:
**gksudo gedit /etc/hostname /etc/hosts**
or you can use the GUI network config tool like the link risbac posted says.

---

### Post by monktbd on 2006-09-11
> **steve.horsley said:**
> 
This will leave him unable to use sudo to do any more administrative work. You **must** change the contents of /etc/hostname and /etc/hosts to match.

oh!
i didnt know that :).

is that gnome related, sudo related or ubuntu related?

---

### Post by Najand on 2006-09-11
Yeah, that is right... It is a sudo matter, I think... Many users have the same problem.

---

### Post by monktbd on 2006-09-11
so i checked a little bit:

sudo uses gethostbyname() and that seems to cause the problems i guess.
now in sudoers you can specify the hosts from where the user to use sudo can be logged in.
normally it says ALL there.
so it shouldnt matter.

but it obviously does?
i guess  i will try that when i am home :)
my recovery mode needs to be tested as well :p

---

### Post by Arevos on 2006-09-11
Is there anything wrong with clicking on System -> Administration -> Networking, entering your password, then clicking on the General tab and typing in a new hostname into the textbox provided? It seems that advocating console commands for something that can trivially be changed through the GUI is complicating matters. Is there a reason not to do it via the GUI?

---

### Post by monktbd on 2006-09-11
> **Arevos said:**
> Is there anything wrong with clicking on System -> Administration -> Networking, entering your password, then clicking on the General tab and typing in a new hostname into the textbox provided? It seems that advocating console commands for something that can trivially be changed through the GUI is complicating matters. Is there a reason not to do it via the GUI?

there is surely nothing wrong at all with it.
it is probably for most the easiest way to do it.

but there are users (like myself) who come from other linux distributions and are usually used to the commandline. these commands are universal compared to certain GUI applets in the menus.

so i knew how to do it via the commandline but not where to look in the menus (and since i sit at work in front of a windows machine i cannot go look as well :)).

---

### Post by Metacarpal on 2006-09-11
> **steve.horsley said:**
> [SIZE="6"][COLOR="Red"]Nooooo!!![/COLOR][/SIZE]

This will leave him unable to use sudo to do any more administrative work. You **must** change the contents of /etc/hostname and /etc/hosts to match. You can either do this by:
**gksudo gedit /etc/hostname /etc/hosts**
or you can use the GUI network config tool like the link risbac posted says.

Good catch.  I saw the title of this thread and thought, oooh - now look for one called "Sudo stopped working after I changed my hostname"...

---

### Post by Mimsy on 2006-09-11
> **Arevos said:**
> Is there anything wrong with clicking on System -> Administration -> Networking, entering your password, then clicking on the General tab and typing in a new hostname into the textbox provided? It seems that advocating console commands for something that can trivially be changed through the GUI is complicating matters. Is there a reason not to do it via the GUI?

I hope not, because that's how I did it... it was the easiest way, and I naively assume that anything done through the GUI is less likely to break important files. :) 

/Mimsy

---

### Post by monktbd on 2006-09-12
ok i tested it on my computer now:

i changed the hostname with
sudo hostname newname

that made sudo not working.
gnome itself was working not well either.
restarted gnome.
gnome worked better but of course sudo still wasnt working.
then just rebooted (without recovery mode) and the old hostname got set again, making sudo useable again.

so now: is that the expected behaviour that a reboot fixes the issue?

---

### Post by Arevos on 2006-09-12
Ubuntu sets its hostname from /etc/hostname each time it boots up. As I understand it, you have to add an alias in /etc/hosts to the new hostname as well in order for sudo to work.

I'd just do it via the GUI, myself.

---

### Post by Mimsy on 2006-09-12
KISS.....? :-\" <-- innocent whistle

/Mimsy

---

### Post by monktbd on 2006-09-12
> **Arevos said:**
> Ubuntu sets its hostname from /etc/hostname each time it boots up. 

actually in my case it was the other way round.
the name in /etc/hosts was set back to /etc/hostname which i changed before with the hostname command.

what i find funny/good/odd is that a plain reboot solved the issue. no need to go to the recovery mode to fix /etc/hostname or /etc/hosts depending which one has the wrong settings.

---

### Post by Metacarpal on 2006-09-13
(Love your sig, monktbd)

---

### Post by mokmoki on 2006-09-13
hmmm, thanks for the help, i eventually used the GUI... i'm a linux newb ^_^

---

### Post by 3rdalbum on 2006-09-13
I had the sudo problem after changing the hostname with the GUI. Be careful; only change it when there's a really good reason to!

---

### Post by Mimsy on 2006-09-13
Such as "I want it too have a cool name"? ;-)

I've had no sudo problems at all since making the change, and I've used the command plenty of times since then. Is there any documentation available as to why the problems start? Is there a common factor, a variable that always seems to be present? It could be useful to know.

Thanks,
Mimsy

---

### Post by Arevos on 2006-09-13
I haven't had any sudo problems changing my hostname via the GUI either. The problems possibly arise when the hostname isn't aliased to 127.0.0.1, and that's controlled by the hosts file. It's worth taking a look at /etc/hosts if you have sudo problems after changing your hostname, and seeing if your new hostname is in there.

---

### Post by monktbd on 2006-09-13
> **Metacarpal said:**
> (Love your sig, monktbd)

thanks :).
i just find it amazing how often the same problem gets solved, especially in this forum here and how often everybody still gets a step by step description.
this is an amazing sign of patience within this community, probably also due to its size.
but then searching online for a solution isnt always easy for an absolute beginner, a question in a forum is then maybe not only the easier solution but also the more successful one.
ok now that was offtopic - sorry.

---

