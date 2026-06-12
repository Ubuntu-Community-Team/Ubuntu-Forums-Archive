---
title: "Repeated Segmentation Faults when installing anything"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Oak37 on 2008-02-01
Hi,
Recently I keep getting segmenation faults (core dumped) errors when installing new programs through synaptic. It has only started recently but means that programs aren't installing properly and hence aren't running. Anybody have any ideas how I can go about fixing this?
I'm running Feisty 7.04

---

### Post by jan quark on 2008-02-01
can you post the exact error message pls
thank you

---

### Post by Oak37 on 2008-02-01
As an example I've recently tried installing clamav. I did this through synaptic and it gave me these errors:
E: clamav-base: subprocess post-installation script killed by signal (Segmentation fault), core dumped.

Thanks for the reply :)

---

### Post by ByteJuggler on 2008-02-01
Can you run the memory test available on the bootup menu and make sure you dont have memory problems.  If you're getting random segmentation faults (in windows terms "access violations") that's indicative of possible hardware problems.

---

### Post by jan quark on 2008-02-01
did you get this error message with every application you try to install via synaptic?

pls run 
```
strace synaptic
```
it should display many code lines and look for an error like core dump if you find one please post the output in code brackets here 
thank you

---

### Post by Oak37 on 2008-02-01
I ran strace and tried reinstalling clamav, there was a lot of text so I picked out the last few lines:
> open("/root/.synaptic/options", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 17
close(17)                               = 0
close(20)                               = 0
kill(19813, SIGTERM)                    = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
rt_sigreturn(0x11)                      = 7197120
exit_group(0)                           = ?
Process 19618 detached


---

### Post by jan quark on 2008-02-01
well there is a second possibility but it is time consuming

you know core dumped can have hundreds of reasons, accordingly to the application it evokes 

but segmentation faults may crop up because of defected hardware memory

try to reboot and launch memtest86+ from the grubloader, it's a time consuming process 

so perhaps before you do this check out google by simply typing  [I]segmentation fault core 

dumped[/I] how many different error threads you get...sry that I cannot give you a click-this and ready solution

---

### Post by Oak37 on 2008-02-01
I was going to run a memory test as ByteJuggler suggested too so I'll start that now. Thanks for you help, both of you. The computer I'm having the seg faults on isn't my main pc so it can afford to have some downtime! :)

---

