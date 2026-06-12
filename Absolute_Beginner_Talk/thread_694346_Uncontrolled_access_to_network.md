---
title: "Uncontrolled access to network"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by very_new_user on 2008-02-11
when I start Ubuntu, login and don't do not start any program at all, Ubuntu itself keeps recieving information from network and keeps sending information to the network. 
On average rate 20 Mb per hour of SENT information (in blocks of 1 Mb). and 3-5 Mb received per hour (received continuously in small packages). 
Finally, every evening I have 150-200 of sent Mb even if I did not use internet the whole day. 

So the questions: 
1) How to stop these both: information sending and receiving? 
2) How to find out what program is doing this and which host it keeps connecting? -- There is no option in "System monitor" to see sent or received bytes by each process. 
3) How to turn OFF the automatic Ubuntu updates? In the 'Update Manager' the "preference" button simply does not exist, though the corresponding help section claims the button should be there. 


Laptop, AMD64, Ubuntu 7.10, 
only basic (default) installation of ubuntu. 

Thanks,

---

### Post by PeterJS on 2008-02-11
> **very_new_user said:**
> when I start Ubuntu, login and don't do not start any program at all, Ubuntu itself keeps recieving information from network and keeps sending information to the network. 
On average rate 20 Mb per hour of SENT information (in blocks of 1 Mb). and 3-5 Mb received per hour (received continuously in small packages). 
Finally, every evening I have 150-200 of sent Mb even if I did not use internet the whole day. 

So the questions: 
1) How to stop these both: information sending and receiving?

Kinda hard to say with out knowing what the source is, see 2
> 
2) How to find out what program is doing this and which host it keeps connecting? -- There is no option in "System monitor" to see sent or received bytes by each process. 

To find what is sending data run:
```

netstat -utp

```
and to see what is receiving data
```

sudo netstat -lutp

```
> 
3) How to turn OFF the automatic Ubuntu updates? In the 'Update Manager' the "preference" button simply does not exist, though the corresponding help section claims the button should be there. 

The documentation is probably for 6.06, the official documentation on get updated when the new LTS comes out. The setting is in System > Administration > System Sources > Updates these days.

---

