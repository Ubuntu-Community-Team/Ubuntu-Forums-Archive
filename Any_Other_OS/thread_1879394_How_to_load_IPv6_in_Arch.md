---
title: "How to load IPv6 in Arch?"
date: 2011-11-11
forum: Any Other OS
---

### Post by ratcheer on 2011-11-11
I am a newbie at Arch. I have a lot of trouble getting straight answers in the Arch forum, so I will try here.

First, I verified that I could not access IPv6 WAN addresses from Arch. Then, I searched the Arch forum and found that I should add ipv6 to the modules array in /etc/rc.conf. I did that and rebooted. I still could not ping an IPv6 web site.

On a hunch, I ran "sudo modprobe ipv6". Then, IPv6 worked just fine.

So, I have two closely related questions. 1) Why didn't adding ipv6 to rc.conf do the same thing as modprobe? 2) How am I supposed to setup Arch so that ipv6 is loaded, automatically at startup?

Thanks,
Tim

---

### Post by boast on 2011-11-11
have you checked for any ipv6 settings in /etc/modprobe.d/modprobe.conf that could be disabling it on boot?

---

### Post by ratcheer on 2011-11-11
> **boast said:**
> have you checked for any ipv6 settings in /etc/modprobe.d/modprobe.conf that could be disabling it on boot?


I will go look, but unless they came with the default install, I didn't put them there.

Tim

---

### Post by ratcheer on 2011-11-11
Yes, thank you very much, @boast. That was it. I wonder why it is blacklisted by default?

Tim

---

### Post by m_duck on 2011-11-11
ipv6 loads automatically for me, but I suspect that it is something I am running that loads it automatically. The fact that it loads when you modprobe it suggests that it may be a syntax error or something in your rc.conf, unless of course there is something in /etc/modprobe.d somewhere that is stopping it. On my system there is nothing there by default that would stop it loading.

If there is nothing suspicious in the above folder, could you post your rc.conf?

EDIT: Too slow :p Glad you got it sorted. Not sure why it is blacklisted on your system. How long ago did you install? There may be a certain package you have installed that has added the blacklist if ipv6 wasn't cooperating with it at some point. Just speculating though.

---

### Post by ratcheer on 2011-11-11
I installed it in early October.

Tim

---

