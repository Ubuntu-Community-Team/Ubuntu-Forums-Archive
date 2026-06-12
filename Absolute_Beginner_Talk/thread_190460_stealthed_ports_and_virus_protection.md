---
title: "stealthed ports and virus protection"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by linux_student_user on 2006-06-06
Im new to Linux, I have everything up and running and have customised my ubuntu desktop extensively - i've deleted windows and am happy with linux :-) well my question is, I ran an online check before installing Firestarter, well it said that some of my ports are stealthed - but i have no firewall yet? - I know linux is very secure but it just seems odd - im running the latest release of ubuntu dapper drake, i was also wondering what other extra security measures should I take, and also what about maintanence? I know linux is resistant to fragmentation - what about cleaning up my disk and increasing performance. thanks in advance.

Mike

---

### Post by jamesford on 2006-06-06
firstarter is just a gui frontend for iptables, which already runs in the background...as far as i know. i dont keep firestarter running, i just start it once in a while when i need to edit a rule (like opening a torrent port or something) and then close it again. and yes the rules stick even if you never run firestarter again.

ive had linux fo about a year now and theres no need for cleanups of any kind

the best security measure you could take i guess is to pick a strong password

---

### Post by ProjectGod on 2006-06-06
general clean up would be i guess... after downloading packages from multi/universe you can clean out the cache which saves about 2/5 to 1/2 of space... if you were to leave the packages in the systems cache

df -m
sudo apt-get clean
df -m

you should see increased "spare" space...

i guess it depends on your machine's capabilities... i have a slow machine so a lighter window manager was magic! **xfce**, or perhaps **icewm** both available on multi/universe.

increasing security... well for starters i guess you could (i've been recommended many times on this forum) use aptitude / synaptic instead of apt-get because sometimes some server services / modules get left behind and they tend to have open ports... such as apache which gets installed as a dependency for numerous other packages... the thing with using apt-get is that it doesnt handle dependencies as well as the other two mentioned utilities... and when removing unwanted packages... it tends to leave behind residue.

:mrgreen:

---

### Post by steve.horsley on 2006-06-06
If it says some of your ports are stealthed, then either the internet was dropping packets while the test was being run due to congestion, or your ISP is filtering certain ports.

I presume all the ports it didn't report as stealthed showed as closed (unless you have installed sone server software) because Ubuntu doesn't run any listening services in its default install. Hence not needing a firewall on the default install.

As for cleaning up your disk - you could try uninstalling packages you don't need, but unless you are short of disk space, is it worth the effort - it won't increase performance. Increasing performance - I don't know how.

---

