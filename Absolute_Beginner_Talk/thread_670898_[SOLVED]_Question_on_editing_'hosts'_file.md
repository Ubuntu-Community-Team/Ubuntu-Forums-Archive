---
title: "[SOLVED] Question on editing 'hosts' file"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by MoonStomper on 2008-01-17
is it possible to include port numbers in host file entries? this is for accessing devices via terminal server. normally, i would do a reverse telnet to an IP, say 192.168.1.1 <port#>. i tried entering "192.168.1.1:2001 DEV1" but it didn't work. any advice would be much appreciated. thanks!

---

### Post by mattismyname on 2008-01-18
No, you can't do that.  It wouldn't make sense.

The hosts file is for mapping names to ip addresses only.  

What exactly are you trying to do?  Access a windows box from an Ubuntu box?  Access an Ubuntu box from a Windows box?

Also, what do you mean by "reverse telnet"?  That is not really a term people would understand.

---

### Post by MoonStomper on 2008-01-18
basically, i have a terminal server (cisco router) which has console connections to my other devices. i configured it in such a way that each console line is mapped to an ip ddress, 

reverse telnet is just a telnet to an IP with a specified port like "telnet 192.168.1.1 2001". this launch a telnet to my terminal server with an IP of 192.168.1.1 and connect me to the device patched to console port 1. For the device in console 2, it would be 192.168.1.1 2002, and so on. 

i'm now thinking of a convenient way, if possible, to telnet directly to my devices without keying the IP + port combo like "telnet webserver" (instead of  "telnet 192.168.1.2001").

thanks for the prompt reply btw. cheers!

---

### Post by mattismyname on 2008-01-18
I think I see.

Is it possible to configure the terminal server to give each device its own separate IP but have telnet always listening on the same standart port?  Then you could put entries in your /etc/hosts to map the different IPs to the names you want for the machines.

Of course, there is probably a much simpler solution to this, just make some aliases in your shell.

Edit your .bashrc and add some lines like:
alias webserver='telnet 192.168.1 2001'

Then "source ~/.bashrc" and if you type 'webserver' at the prompt, it should execute the telnet command.

---

### Post by MoonStomper on 2008-01-18
....and it worked like a charm! sweeeeeeet!  \\:D/  things have just become a little more convenient! this is one of the reasons why i won't regret moving to ubuntu. :D 2 thumbs up to u for the help! =D>

---

