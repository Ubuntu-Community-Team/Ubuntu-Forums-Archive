---
title: "my solved problems with Firestarter"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by solotransit on 2006-08-05
Hello, 
Ive seen heaps of posts around on the forums about issues with firestarter. i have managed to solve mine so far, so i hope sharing this will help. My first post i think! :D 

note: im running dapper with gnome

first, i have learned that a firewall is acually already build into ubuntu,it is called IPtables. 
it is the set of rules a firewall has, without the gui. 
hardcore people use it alone from what i have gathered. 

firestarter is one gui that makes it easier for newbies like me to configure it. one of the few times i have seen the word 'wizard' in ubuntu so far. 

ok, so thinking it was a firewall in itself (and wasnt running hidden as it is), i searched for a way to make it start on boot up. firestarter is just the tool for configuring the firewall, just because its not in the icon notification area, doesnt mean its not running.
In my newbish ignorance, i followed the instructions on a post that was meant to set firestarter to open on log-in. the post basically had me edit the SUDOERS file, to set, what appears to be, the program to be run out of sudo.

It didnt work, for whatever reason, and recently my firestarter has not been working. there are many posts about this, involving a gtk error, and the gui of firestarter not opening. reinstall didnt help, complete removal didnt complete.

I remembered the sudoers edit i had made months ago and remarked out the part i had added (# at start of line). worked straight away after.

i hope this helps anyone else who has had trouble.

good luck. :)

---

### Post by Anduu on 2006-08-05
Excactly!

---

