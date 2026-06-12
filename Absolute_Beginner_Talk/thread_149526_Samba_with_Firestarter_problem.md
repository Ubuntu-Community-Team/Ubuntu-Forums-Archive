---
title: "Samba with Firestarter problem"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by Tim Thumb on 2006-03-24
I've just set up Samba as a file server to 3 WinXP machines. The 3 Win machines were originally set up like this:

1 with a static IP
2 using DHCP

The Ubuntu box is running DHCP which I believe is the default.

So, for all 3 Win machines the file sharing works fine when Firestarter is switched off. When it's on no machine can get through - as it should be. When I add the IP of the machine with the static IP as a rule that machine gets through OK.

So logic would tell me to assign static IPs to the other 2 machines and add a rule for each in Firestarter. Tried this but it didn't work and I can't for the life of me work out why.

Any help much appreciated.

---

### Post by Tim Thumb on 2006-03-26
I worked this out with the help of another thread by doing this:

Firestarter/Preferences/Advanced options/Broadcast traffic and untick "Block broadcasts from external network"

Everything works perfectly now although I have no idea what this has actually done. I also don't know why it was needed for 2 of my Win machines and not the other.

---

