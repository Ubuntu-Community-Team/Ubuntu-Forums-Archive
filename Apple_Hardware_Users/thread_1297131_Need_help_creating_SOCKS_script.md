---
title: "Need help creating SOCKS script"
date: 2009-10-21
forum: Apple Hardware Users
---

### Post by janthes on 2009-10-21
Hi folks,

OK, this is broken up into two parts:

I'm trying to create a script on my Macbook that does two things, get my WAN IP, and create a SSH SOCKS proxy using the IP. The first part to my script, getting the IP and dumping it to a txt file, works. The second part, creating the tunnel is giving me a lil' headache. What I want the script to do is open a SSH tunnel using the IP in the txt file. I'm stuck on this part. 

The second part I'd like to do with this script is have a simple menu at launch. I'd like the menu to ask if I want to copy the IP and quit, or start a tunnel using the IP saved. I don't even have the faintest idea were to start with scripting this.

My rough draft code is as follows:

```

#!/bin/bash

# Script to get WAN IP and create a SOCKS proxy to my network


# Gets home WAN IP.

clear
echo Quering for local WAN IP.
echo
echo Local WAN IP is:
lynx -dump http://whatismyip.org > ~/WAN_IP.txt
cat ~/WAN_IP.txt
echo 
echo A copy called 'WAN_IP.txt' has been placed in your home folder.
exit


# Creates tunnel
clear
echo Attempting to create tunnel using IP found in 'WAN_IP.txt'
echo
ssh -ND 80 -p 443 server@ [pull IP from WAN_IP.txt]
echo
echo Happy surfing!

```

BTW, I don't have any issues with the SSH command when imputed manually with an IP. Help would be appreciated, thanks!!

---

### Post by janthes on 2009-10-22
bump

---

### Post by janthes on 2009-10-25
bump

---

### Post by janthes on 2009-10-27
Hints, anyone?

---

### Post by janthes on 2009-11-02
...anyone???

---

