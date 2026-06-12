---
title: "Ruby 1.8.6 on Ubuntu 6.06 ?"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by nhinze on 2007-07-19
Dear all,

how do I upgrade my current ruby version:

deploy@ubuntu:~$ ruby -v
ruby 1.8.4 (2005-12-24) [i486-linux]

to ruby version 1.8.6 ? When I use apt-get upgrade ruby it says it is already at the newest version.

Thank you,

Nick,

---

### Post by FleetAdmiral74 on 2007-07-19
You could go to their site and see if they either have a pre-compiled deb package, or the source files. Might have trouble tracking dependencies with the latter though.

I am sure Gutsy (released in October) will have the newest version available in the repos. I am waiting on Pidgin myself :)

oh crap, you have one bean...you could be new and totally not know what I mean...um...sorry!

---

### Post by JesterDev on 2007-07-20
Actually I remember seeing something about there being a ruby 1.9.X or something along those lines. Try the synaptic package manager instead - System|Administration|Synaptic Package Manager. Then again I could be wrong. 

As far as I know there is nothing major for the small jump from 4 to 6 so you should be just fine.

---

### Post by Heliix on 2007-07-20
> **JesterDev said:**
> Actually I remember seeing something about there being a ruby 1.9.X or something along those lines. Try the synaptic package manager instead - System|Administration|Synaptic Package Manager. 

I agree.
'sudo apt-get install ruby1.9' should find and install the newest ruby1.9 version (with all dependencies, of course). you may need to update your package list by 'sudo apt-get update'.

then check the version...
hela@electra:~$ ruby -v
ruby 1.8.4 (2005-12-24) [x86_64-linux]

what? still version 1.8.4? OK, we'll make an alias to specify what version of ruby we want:
hela@electra:~$ alias ruby='ruby1.9'
hela@electra:~$ ruby -v
ruby 1.9.0 (2006-06-08  [x86_64-linux]

to make an alias permanent, add the line "alias ruby='ruby1.9' " to your .bash_profile or .bash_aliases file.

---

