---
title: "if i'm not running as administrator...or..."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2007-11-11
if i'm not running as administrator...or... create a second user just for peer2peer,torrent downlooading and trying some apps,things etc around in order to protect my personal data... is it safe enough... or some apps,networking activity...whatever.. could bypass my main account(and the data?

also if someone know how to make firestarter usable to non admnistrative users... or make some default general rules when im not around(near my computer)?

---

### Post by SunnyRabbiera on 2007-11-11
well technically with the Sudo system everyone can be administrator if you set things that way.
the thing is that a sudo based system eliminates the root account from the equation, this is both a positive and a negative in my mind but I also know the drawbacks of a root system as well.
Sudo works almost how administration works on windows, with the first account having the primary permissions turned on by default, however you still need passwords to install new packages and access the core of your system.
In this case sudo is better then how windows works, in windows it assumes that everyone has enough brains to run the system with little or no support and as a result windows has become virus city.
sudo safeguards the system core far better, but I can see where it can be flawed.
The root system of most linux distributions can be considered better from a security point of view, in a root based system only the root can have full access to the system.
The other users on the root systems are not allowed to do anything with the core of the OS without becoming root via the terminal or logging in as root.
However despite how good it sounds to just have a root account and just eliminate whatever else on there it is very bad to run under root... in this case a root system can also become just as bad as a MS system, where people could hack into the core and cause serious damage.
In a root system it is wise never to log in as the root account unless it is needed, in the root based versions of linux I have used i only had to use root a good 1 out of 10 times... but only to have easier access to edit certain factors of my system without touching the terminal.
the biggest drawback I see to a sudo system is that the password of the initial account is also the password of the root account and it is best to change your password frequently on a sudo based system.

---

### Post by someoneouthere on 2007-11-11
ok understood... so can i make some general changes to whole desktop(for all users)???
and  can i run firestarter as non root? is this possible?
because whenever i run with no administrative rights i can't run firestarter....

---

