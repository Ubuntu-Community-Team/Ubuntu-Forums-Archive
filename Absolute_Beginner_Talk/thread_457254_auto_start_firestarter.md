---
title: "auto start firestarter"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by JParkus on 2007-05-28
just wondering how to make firestarter start  when i start the computer

---

### Post by PetePete on 2007-05-28
it loads the rules into iptables which is the firewall that gets started when ubuntu boots.

you dont need to run the firestarter program to be protected.... dont believe me, test it yourself ;)

---

### Post by techno-mole on 2007-05-28
ive read loads of posts about people who want to install anti-virus programs and firewalls, and it may be true that you dont need them because of the way linux is built and so on, but i guess in this day and age people just like to feel safe.
ive also heard that if your installing things like wine or networking with windows pc's then maybe its an idea to have some sort of protection.
i have installed avg and firestarter - to get firestarter to run at start up i went to --> system --> preferences --> sessions --> click new and then put firestarter in the name field and then in the command field put --> sudo firestarter --start-hidden
and then save it and that should do it, this is how they say to do it on the ubuntu fiesty guide, so if its wrong ill say sorry now :D
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_Firestarter_start_automatically_at_startup](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_Firestarter_start_automatically_at_startup)
cheers

---

### Post by ramjet_1953 on 2007-05-29
I know that it is difficult for "Windows Refugees" to let go of old habits, but try to do it anyway.

Firstly, why do you need to use Firestarter to modify iptables?

Do you have any special requirements, like video conferencing or something that needs to re-map ports?

Remember Firestarter is NOT a firewall. It is a tool for modifying iptables.

By default, all ports are closed and the system is secure.

**_Remember this well_**. Any application for modifying iptables must be run with root priviliges, and having it start-up and run continuously is a grave security risk.

Leave well alone and just enjoy Linux.

Regards,
Roger :cool:

---

