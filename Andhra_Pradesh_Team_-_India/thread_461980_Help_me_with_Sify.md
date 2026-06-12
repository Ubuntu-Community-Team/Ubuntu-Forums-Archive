---
title: "Help me with Sify"
date: 2007-06-02
forum: Andhra Pradesh Team - India
---

### Post by gupta_sumesh63 on 2007-06-02
:( I have recently installed UBUNTU 7.04 feisty fawn. I am a subscriber to sify broadbad. I do not know how to download their Sifyconnect software and install it. What they offer is a .rpm file. I do not have alien installed since I cant connect to the net. Please help me resolve my problem. I tried to download the file from Windows, copied it to UBUNTU, asked someone to convert it to .deb and mail me back and tried to install it on UBUNTU. But alas, I as told that the sifyconnect pkg v30 reqiures newer packages of libc6, libglib etc. There is no response from Sify too. Can anyone here help me? I am new to Linux.

---

### Post by abhiomkar on 2007-06-03
You can download the tar.gz file from [http://210.18.11.199:81/bbandclient/sifyconnect-1.3-bin.tar.gz](http://210.18.11.199:81/bbandclient/sifyconnect-1.3-bin.tar.gz)

extract it :
```
tar -xzvf sifyconnect-1.3-bin.tar.gz 
```

install it :
```
cd sifyconnect-1.3-bin/
chmod +x install.sh
./install.sh

```

run sify dialer & login with your sify account :
```
sifyd
sifyconnect -l
```

You can login with one command :
add this line to ~/.bashrc file
```
alias sify="sifyd && echo -e 'accountname\npassword' | sifyconnect -l"
```

Just Run 'sify' command whenever you start ubuntu

Also check it out : [http://www.ubuntu-in.org/wiki/Broadband_Howto](http://www.ubuntu-in.org/wiki/Broadband_Howto)

---

### Post by sajiv_k on 2007-08-12
I tried all these commands in Ubuntu.

Cant open any site, but i can ping their gateway and DNS servers and get 100% success.

Called up Sify customer care they sent in an engineer who told me that he doesn't know anything about Linux.

So now I have to fix up on my own.

Any idea whats wrong?

---

### Post by sajiv_k on 2007-08-18
I tried a work around and now I can connect.

Since I have got dual boot I connected in Windows and restarted the computer. When I got a 
prompt from the Sify dialer to disconnect I canceled it.

When the system booted in Ubuntu the connection was working !!!

I guess theres something wrong with the Sify dialer for Linux.

---

### Post by tus on 2007-08-22
Hello,
i have a problem with SIFY net over UBUNTU.I just installed UBUNTU 7.04 on my disk.
 Here is my effort.
 I successfully installed install.sh file

tushar@tushar-desktop:~$ sify

 

sifyconnect  sifyd       

 

tushar@tushar-desktop:~$ sifyd

 

tushar@tushar-desktop:~$ sifyd

 

Sify broadband daemon already running...

 

run sifyconnect --login to login)

 

tushar@tushar-desktop:~$ sifyconnect -l

 

Welcome to Sify BroadBand Service

 

 

 

username :tisai162tushar

 

password :
Now what  should i do ?????
FEw day's before i got error like 
Unable to Connect Sify Access Manager ::: No route to host
But now i don't get this error also.(after entering  password)
i ping my network also.And i think there is no any error.

---

### Post by sajiv_k on 2007-08-22
Tushar even I have the same problem, after passowrd nothing works. 

Its their damn dialer.

Some one suggested me to use pppoe I did that but it still doesnt work for me but you can try

In the terminal  type

**sudo pppoeconf**

and follow the steps It may help.

I have posted this query in the Networking forum as well 

[http://ubuntuforums.org/showthread.php?t=530950](http://ubuntuforums.org/showthread.php?t=530950)

---

### Post by snailbomb on 2007-08-23
This might be of your help on Ubuntu ... It did help me and it works ... I use ubuntu 7

[http://aguywitha.com/_main/sify-boradband-on-linux-p/]("http://aguywitha.com/_main/sify-boradband-on-linux-p/trackback/")

Thanks!!!

---

### Post by sajiv_k on 2007-08-24
Thanks for the info

But the link for that file is broken

I have found out something [here]("http://sourceforge.net/project/downloading.php?group_id=157014&use_mirror=nchc&filename=antidialer_0.2-1_i386.deb&16449360")

Haven't tried it would post the outcome after trying.

---

### Post by snailbomb on 2007-08-24
i messaged the author of the blog and just checked it out the links fiixed ... 

Cheers

---

### Post by sajiv_k on 2007-08-24
Thanks mate :-D 

It finally worked !!!!!!!!!!!!!!!

Only issue is that I get this error message when I run 

```
sudo sifyconnect -login
```

at the terminal

> You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option.

Any idea whats causing this ???

I really don't care coz my connection is working now :lolflag:

p.s. That antidialer mentioned in the last post didnt work :(

---

### Post by tus on 2007-08-25
My gateway is not pinging.

Here is my effort

root@tushar-desktop:/home/tushar# ping 10.12.227.1

PING 10.12.227.1 (10.12.227.1) 56(84) bytes of data.

From 10.12.227.162 icmp_seq=2 Destination Host Unreachable

From 10.12.227.162 icmp_seq=3 Destination Host Unreachable

From 10.12.227.162 icmp_seq=4 Destination Host Unreachable

From 10.12.227.162 icmp_seq=6 Destination Host Unreachable

From 10.12.227.162 icmp_seq=7 Destination Host Unreachable

From 10.12.227.162 icmp_seq=8 Destination Host Unreachable

I think my LAN card is not detected by UBUNTU .
What should i do????????????/

From 10.12.227.162 icmp_seq=10 Destination Host Unreachable

From 10.12.227.162 icmp_seq=11 Destination Host Unreachable

---

### Post by riyazuddins on 2007-10-21
Hello Everybody,

            Solution for SifyBB users.

download the sifybb client. don't know how to download? call customer care.

            OR

```
http://www.geocities.com/sanjulu_great/sify_bbclient-3.0.tar.gz
```


save it and extract. go to Applications->Accessories->Terminal

change the directory to where you extracted .tar.gz file. ( cd Desktop/sify_bbclient-3.0/ )

now type sudo sh install.sh

you will get a message sifybb successfully installed.

now type in terminal sudo sifyconnect

Here some troubleshooting required if you get following error messages.

1. sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory

Solution: sudo ln -s /usr/lib/libssl.so /usr/lib/libssl.so.4

2. sifyconnect: error while loading shared libraries: libcrypto.so.4: cannot open shared object file: No such file or directory

Solution: sudo ln -s /usr/lib/libcrypto.so /usr/lib/libcrypto.so.4


Now type in terminal: sudo sifyconnect
asks for password enter password. a nice GUI will appear asking sifyBB login information. enter user ID and password click login that's it.

---

### Post by bharadwaj on 2008-01-25
this whole thing is ****. I was a sify user earlier. The sify client only works on red hat based systems. For Ubuntu call up your local sify internet callcentre and ask him to bypass your connection. later you will be given with one ip i don remember but its something like
202.144.65.70:8090/login_rest.php
you open the page login in the browser to get your online bandwidth.

---

### Post by LequidMetal on 2008-11-17
Hi,

    I am a new Ubuntu user . I have just installed Ubuntu 8.10 . I have been trying to install a proper dialer for Sify unsuccessfully .(And) Yes i have read through the previous posts and also threads relating to this issue here .
I just have a few questions to ask

--> Which Sify Dialer is best for Ibex  ?
--> Would it compromise my Password and such details?
--> Most importantly , Does it work 100% ?

I am a complete n00b so i would really appreciate some detailed Guidance .

-D

---

### Post by LequidMetal on 2008-11-23
The default sify client provided by Sify works just fine in Ubuntu ... It also has a GUI ....... Absolutely ok

---

### Post by Xcalliber on 2008-12-24
Hye Guyz,
        So after 5 days of searching through all the forums I was finally able to browse internet from my Ubuntu 8.1 using Sify dialer.

But I get disconnected avery 10-25 min. Dont know whatz causing it because I have not installed any firewall or anything ....

Have any of you faced this problem ?

---

### Post by grif.ghatak on 2009-02-12
> **Xcalliber said:**
> Hye Guyz,
        So after 5 days of searching through all the forums I was finally able to browse internet from my Ubuntu 8.1 using Sify dialer.

But I get disconnected avery 10-25 min. Dont know whatz causing it because I have not installed any firewall or anything ....

Have any of you faced this problem ?
Forget dialers... forget hassle .... 

try this thread: [http://ubuntuforums.org/showthread.php?p=6721614#post6721614](http://ubuntuforums.org/showthread.php?p=6721614#post6721614)

---

### Post by indanger on 2009-10-28
Hi,
 
Even I am facing a very peculiar problen with Sify Broadband Client, whenever I cliked it to connet to internet without asking for my username/pwd it logs me in, though auto login is not enable and to get rid of this error I uninstalled the Broadband client and re-installed it on my system but I am still facing the same issue.Could you help me in solving this problem.
 
 
Regards,
D

---

### Post by gauthamnagpur18 on 2012-01-21
Hi ,

Thanks for valuable information . Sify client got installed in my Ubuntu 11.10 but when i try to run its throwing error:

sifyconnect: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory

I tried the below command but it also failed .

neli@ubuntu:~$ sudo ln -s /usr/lib/libssl.so /usr/lib/libssl.so.4
[sudo] password for neli: 
ln: creating symbolic link `/usr/lib/libssl.so.4': File exists

Could you please help me out .

---

