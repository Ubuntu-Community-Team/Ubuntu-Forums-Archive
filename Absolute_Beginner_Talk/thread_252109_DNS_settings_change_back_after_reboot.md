---
title: "DNS settings change back after reboot"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by minj on 2006-09-06
To correctly access internet I need 2 ips included in System->Administration->Networking->DNS->DNS Servers.
But those are gone and I have to reinclude them in the list every time I reboot. How do I make those permanent?

---

### Post by tomBorgia on 2006-09-06
set the DNS up in resolv.conf then edit your /etc/dhcp3/dhclient-script

you need to comment out the entire section from

make resolv.conf(){

all the way down to 

}
run_hook

so it looks like this -
#make resolv.conf(){
#
#lots of c...
#
#}
#
run_hook() {

Don't comment out the run_hook() bit!!!

---

### Post by minj on 2006-09-06
It worked. Thank you.

---

