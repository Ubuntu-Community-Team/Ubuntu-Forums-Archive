---
title: "nfs shared folders"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by cinderella on 2006-10-18
[COLOR="Red"]Okay Im begging Someone pls help me!!![/COLOR]
I need someone to explain in a step by step fashion because the nfs howtos confuse me.

I have 3 problems but first let me describe what my project entails.
My project is based on fingerprint indentification. Im using an ATMEL board (which u do not need any knowledge of) to identify my fingerprint. But first I need to setup the board so that I can communicate with it from my Ubuntu PC. The board (my client) runs under Linux OS (kernel version 2.4.19 rmk7). 
This board came with an installation cd. So I installed the content of the cd on by ubuntu PC. The cd contained the following cross compilers, library files, etc and once it was installed two working directories were created: /nfsshare and /mnt/ramdisk

Ok I hope u got that so far. :) 

Now this is how I installed NFS: 

```
sudo aptitude -P install nfs-kernel-server nfs-common portmap 
sudo /etc/init.d/protmap restart
sudo /etc/init.d/nfs-common restart
sudo gedit /etc/exports
sudo /etc/init.d/nfs-kernel-server restart
sudo exportfs -a
```
 
In the exports file I typed the following:
```
/nfsshare 146.230.192.49(rw,all_squash)

```

Then back in my terminal I typed and go the following error:
```
bulletproof@Bulletproof:~$ /etc/rc.d/init.d/nfs start
bash: /etc/rc.d/init.d/nfs: No such file or directory

```

Then I tried and still no luck

```
bulletproof@Bulletproof:~$ /etc/rc.d/init.d/nfs-kernel-server start
bash: /etc/rc.d/init.d/nfs-kernel-server: No such file or directory
```


Then I tried removing rc.d from the command and it worked (I think):

```
bulletproof@Bulletproof:~$ sudo /etc/init.d/nfs-kernel-server start
 * Exporting directories for NFS kernel daemon... exportfs: /etc/exports [3]: No 'sync' or 'async' option specified for export "146.230.192.49:/nfsshare".
  Assuming default behaviour ('sync').
  NOTE: this default has changed from previous versions
                                                                         [ ok ]
 * Starting rpc nfsd...                                                  [ ok ]
 * Starting rpc mountd...                                                [ ok ]




```

[COLOR="Red"]Ok so that is my first qusetion, why can't I get the command working with rc.d. When I listed the files in etc I found rc0.d right up to rc6.d. I even tried typing the command again with the number included as shown below 
```
/etc/rc0/init.d/nfs-kernel-server start
```[/COLOR]

Anyway I carried on without fixing the rc.d problem.
I opened up the terminal for the board and then typed in the following commands:

```
mount -t nfs 146.230.193.109:/nfsshare /mnt/nfs
ls -l /mnt/nfs
```

When typed in the mount command the error read [COLOR="DarkOrange"]mount: RPC: timed out[/COLOR].
When I listed the contents in /mnt/nfs then nothing listed.

So I went back to my ubuntu pc terminal and typed the following:
```
bulletproof@Bulletproof:/$ ls -l /nfsshare
ls: /nfsshare: No such file or directory
```

When I go to Administration--->Shared Folders I can see the nfsshare folder and when i click on properties its path shows as just /nfsshare.

so if it is their then why can i see the contents on the nfsshare folder.

so those are my 3 questions. to summarize, the [COLOR="Blue"]first[/COLOR] question is why does rc.d not work in the command /etc/rc.d/init.d/nfs-kernel-server start

the [COLOR="Blue"]second[/COLOR] question is why does mount: RPC: timed out appear and how do i solve the problem

the [COLOR="Blue"]third question[/COLOR] is why cant i list the contents of nfsshare
](*,) :confused:

thank u in advance all u clever people!!!!!

---

### Post by mips on 2006-10-18
Okay I think your problem with rc.d stems from old Atmel documnetation maybe. I might be mistaked but rc.d is something from 2.4x kernel daysor not used by Debian ([FONT=Verdana][SIZE=1][SIZE=2]/etc/init.d/ with links from /etc/rc[0-56S].d/) [/SIZE][/SIZE][/FONT]? The Atmel documentation is just going to confuse you. Even the package name has changed hence they refer to stuff like nfs start etc which does not exist anymore.

The nfs server you are trying to run only serves the purpose of acting as a file server for the SM01 2.4xkernel.

Please follow this guide wrt the server installation, **[http://www.ubuntuforums.org/showthread.php?t=249889](http://www.ubuntuforums.org/showthread.php?t=249889)**

Just do the  **Install NFS Server Support**  section. You don't need the client config on your ubuntu pc seeing it gonna be a server.

Change the IP addresses accordingly to suite your environment. Also note that they use the /files label instead of /nfssare label. I'm not to sure about this but suggest you use the notation in the guide I linked to.

Let us know how it goes.

---

### Post by bluefrog on 2006-10-18
1) answered by mips

2) most likely portmap is not running if you type this
sudo /etc/init.d/protmap restart   (typo...)

3) your share is not mounted (mount: RPC: timed out.)

James

---

### Post by mips on 2006-10-18
I'm doing a bit of consolodatiing here from [http://www.ubuntuforums.org/showthread.php?t=278939](http://www.ubuntuforums.org/showthread.php?t=278939)


```
bulletproof@Bulletproof:~$ ls -l /nfsshare
ls: /nfsshare: No such file or directory
```

The nfsshare refers to a folder you must have created. You could just as easily use /home as in your home folder.

Where did you save all your development files. I suggest you put them in your /home folder and then use /home as the label in the above guide.

---

### Post by mips on 2006-10-18
> **bluefrog said:**
> 
2) most likely portmap is not running if you type this
sudo /etc/init.d/protmap restart   (typo...)


Yes, thats a typo in the command, use:
```
sudo /etc/init.d/portmap restart
```

---

### Post by cinderella on 2006-10-18
> **mips said:**
> Yes, thats a typo in the command, use:
```
sudo /etc/init.d/portmap restart
```

Thanks I tried :

```
/etc/init.d/portmap restart
 * Stopping portmap daemon... /etc/init.d/portmap: line 54: /var/run/portmap.state: Permission denied
                                                                                            [ ok ]
 * Not starting portmap daemon.  Already running.                                           [ ok ]
```

but I still get the error in my board's terminal

```
[root@SM01 /root]$mount -t nfs 146.230.193.109:/nfsshare /mnt/nfs
mount: RPC: Timed out
```

I also tried typing the following under my home directory but still no luck:

```
bulletproof@Bulletproof:/home$ ls -l /nfsshare
ls: /nfsshare: No such file or directory

bulletproof@Bulletproof:/$ ls -l /nfsshare
ls: /nfsshare: No such file or directory


```

---

### Post by cinderella on 2006-10-18
> **bluefrog said:**
> 1) answered by mips

2) most likely portmap is not running if you type this
sudo /etc/init.d/protmap restart   (typo...)

3) your share is not mounted (mount: RPC: timed out.)

James

so how do i get rid of this [COLOR="DarkOrange"]mount: RPC: timed out[/COLOR] problem

---

### Post by mips on 2006-10-18
If you cd to your home folder and type ls does it list a nfsshare folder ?

Something is wrong with permission on the port map issue. i don't get those errors. Something might have gone wrong with your install.

Here are the Permissions & contents of my portmap.state file:
```
mips@obelix:/var/run$ ls -l portmap.state
**[COLOR=Red] -rw-r--r--[/COLOR]** 1 root root 816 2006-10-18 15:37 portmap.state

reon@obelix:/var/run$ cat portmap.state
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp    931  status
    100024    1   tcp    934  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32784  nlockmgr
    100021    3   udp  32784  nlockmgr
    100021    4   udp  32784  nlockmgr
    100021    1   tcp  44887  nlockmgr
    100021    3   tcp  44887  nlockmgr
    100021    4   tcp  44887  nlockmgr
    100005    1   udp   1010  mountd
    100005    1   tcp   1013  mountd
    100005    2   udp   1010  mountd
    100005    2   tcp   1013  mountd
    100005    3   udp   1010  mountd
    100005    3   tcp   1013  mountd
mips@obelix:/var/run$
```

---

### Post by mips on 2006-10-18
Where does your **nfsshare** folder live ?
1- /nfsshare
2- /home/nfsshare
3- /home/bulletproof/nfsshare

Try and put the full path of nffsahre in your exports file.

---

### Post by cinderella on 2006-10-18
> **mips said:**
> If you cd to your home folder and type ls does it list a nfsshare folder ?

Something is wrong with permission on the port map issue. i don't get those errors. Something might have gone wrong with your install.

Here are the Permissions & contents of my portmap.state file:
```
mips@obelix:/var/run$ ls -l portmap.state
[COLOR=Red] -rw-r--r--[/COLOR] 1 root root 816 2006-10-18 15:37 portmap.state


```

I did try listing the contents of nfsshare in the home directory and i posted my results in this thread. 

I tried to show u my portmap.state but these are the errors i got:
```

bulletproof@Bulletproof:~$ cd /var
bulletproof@Bulletproof:/var$ ls
backups  cache  games  lib  local  lock  log  mail  opt  run  spool  tmp
bulletproof@Bulletproof:/var$ cd /run
bash: cd: /run: No such file or directory
bulletproof@Bulletproof:/var$ ls -l portmap.state
ls: portmap.state: No such file or directory
bulletproof@Bulletproof:/var$ cat port.state
cat: port.state: No such file or directory
bulletproof@Bulletproof:/var$ cat portmap.state
cat: portmap.state: No such file or directory
bulletproof@Bulletproof:/var$
```

But when I type in rpcinfo -p I get :

bulletproof@Bulletproof:/$ rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp   1018  status
    100024    1   tcp   1021  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32881  nlockmgr
    100021    3   udp  32881  nlockmgr
    100021    4   udp  32881  nlockmgr
    100021    1   tcp  59103  nlockmgr
    100021    3   tcp  59103  nlockmgr
    100021    4   tcp  59103  nlockmgr
    100005    1   udp    781  mountd
    100005    1   tcp    784  mountd
    100005    2   udp    781  mountd
    100005    2   tcp    784  mountd
    100005    3   udp    781  mountd
    100005    3   tcp    784  mountd

is this the same thing

---

### Post by cinderella on 2006-10-18
> **mips said:**
> Where does your **nfsshare** folder live ?
1- /nfsshare
2- /home/nfsshare
3- /home/bulletproof/nfsshare

Try and put the full path of nffsahre in your exports file.

I tried all these options already.
I changed it in the exports file and then I saved it and then typed  
exportfs -a  and then restart nfs-kernel-server

Then in the board's terminal I changed this command :

mount -t nfs 149.230.193.109:/nfsshare /mnt/nfs

to 

mount -t nfs 149.230.193.109:/home/nfsshare /mnt/nfs

and 

mount -t nfs 149.230.109:/home/bulletproof/nfsshare /mnt/nfs

but all of these still said mount: RPC: timed out

:confused:

---

### Post by mips on 2006-10-18
> **cinderella said:**
> 
```

bulletproof@Bulletproof:~$ cd /var
bulletproof@Bulletproof:/var$ ls
backups  cache  games  lib  local  lock  log  mail  opt  run  spool  tmp
bulletproof@Bulletproof:/var$ cd /run
bash: cd: /run: No such file or directory


You cannot say cd /run when you are in the var folder. When you specify / in front of a folder name you are basically saying the folder is in the lowest level of the tree / (Don't quite know how to explain this)

You can say cd /var because it takes you to / and then to var. Once you are in /var and you use the / again it's going to try and take you back to / followed by run.

So you can do:
[CODE]cd /var
cd run

or

cd /var/run
```

---

### Post by cinderella on 2006-10-18
sorry that was a silly mistake!!!

I did as u told me I typed cd /var/run
then I typed ls -l portmap.state
the error showed

ls: portmap.state no such file or directory


what does this mean???? it sounds like big trouble. the thing is i dont know how solve the problem if portmapper doesnt work

---

### Post by mips on 2006-10-18
The only thing I can suggest is to follow the guide I posted in the link above to the letter as it works. Just substitude the variables you need changing. Un-install all the packages you installed before you do a re-install.

It's seems something is wrong with your install, what I do not know.
> 
**Install NFS Server Support**
at the terminal type
[COLOR=Blue]***sudo apt-get install nfs-kernel-server nfs-common portmap***[/COLOR]
[COLOR=Red]When configuring portmap do =**NOT**= bind loopback. If you do you can either edit /etc/default/portmap by hand or run:[/COLOR]
[COLOR=Blue][I]sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap restart[/I][/COLOR]

**Editing /etc/exports**
the /etc/exports file is used for creating a share on the NFS server

invoke your favorite text editor or
[COLOR=Blue]*sudo vi /etc/exports*[/COLOR]

Here are some quick examples of what you could add to your /etc/exports

For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255[LIST]
[*][COLOR=Blue]/files 192.168.1.1/24(rw,no_root_squash,async)[/COLOR][/LIST]Or for Read Only from a single machine[LIST]
[*][COLOR=Blue]/files 192.168.1.2 (ro,async)[/COLOR][/LIST]save this file and then in a terminal type
[COLOR=Blue]*sudo /etc/init.d/nfs-kernel-server restart*[/COLOR]

Also aftter making changes to /etc/exports in a terminal you must type
[COLOR=Blue]*sudo exportfs -a*
[/COLOR] 

---

### Post by cinderella on 2006-10-18
thanks i will try uninstalling and re-installing and i wil let u know

---

### Post by mips on 2006-10-18
> **cinderella said:**
> thanks i will try uninstalling and re-installing and i wil let u know

I followed **all **the steps in [COLOR=Blue]**blue**[/COLOR] above and it worked out fine for me.

---

### Post by cinderella on 2006-10-18
> **mips said:**
> I followed **all **the steps in [COLOR=Blue]**blue**[/COLOR] above and it worked out fine for me.

just to double check. How do i unistall everything? Is it sufficient to go to my synaptic package manager and delete the following from the package manager?
 
nfs-kernel-server
portmap
nfs-common and their dependancies

---

### Post by mips on 2006-10-18
Should be ok. you could also do a clean/purge but I cannot remember the exact command syntax

---

### Post by mips on 2006-10-18
[COLOR=Blue]**sudo apt-get clean**[/COLOR] should purge the folders as well. You have to exit synatic in order to run apt-get. Once completed you can start the re-install.

---

### Post by cinderella on 2006-10-18
hi i forgot how to use the vi editor!!!! i knew this 3 years ago

---

### Post by cinderella on 2006-10-18
> **cinderella said:**
> hi i forgot how to use the vi editor!!!! i knew this 3 years ago

ok i think i got it

i pressed "o" to get onto a new line the "i" to insert text and then "Esc" to escape from inserting text then ":wq" to exit and save

---

### Post by cinderella on 2006-10-18
okay i uninstalled and then re-installed and followed everything in blue and still no luck

---

### Post by mips on 2006-10-18
Do you at least have a portmap.state file in /var/run ?

What are your network settings on the PC & the SM01 (IP, Netmask, Gateway etc) ?

---

### Post by mips on 2006-10-18
Found this, [http://www.linuxquestions.org/questions/showthread.php?t=59343](http://www.linuxquestions.org/questions/showthread.php?t=59343)

Do you have a firewall running on Ubuntu by any chance ?

---

### Post by cinderella on 2006-10-18
> **mips said:**
> Do you at least have a portmap.state file in /var/run ?

What are your network settings on the PC & the SM01 (IP, Netmask, Gateway etc) ?

well yes i do have a portmap.state file this is the output:

```
bulletproof@Bulletproof:/var/run$ls -l portmap.state
-rw-r--r-- l root root 156 2006-10-18 22:07 portmap.state
bulletproof@Bulletproof:/var/run$cat portmap.state
     100000    2    tcp     111  portmapper
     100000    2    udp     111  portmapper
     100024    1    udp     701  status
     100024    1    tcp     704  status
```

[COLOR="DarkOrange"]my ip address,netmask, gateway, etc[/COLOR]

Note that my ip address for my pc is 146.230.193.109
and that for my board is 146.230.192.49
```
[COLOR="red"]bulletproof@Bulletproof[/COLOR]:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:20:74:2B:B8
          inet addr:146.230.193.109  Bcast:146.230.195.255  Mask:255.255.252.0
          inet6 addr: fe80::20f:20ff:fe74:2bb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:318988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44267 errors:1 dropped:0 overruns:0 carrier:0
          collisions:4381 txqueuelen:1000
          RX bytes:71020898 (67.7 MiB)  TX bytes:6202859 (5.9 MiB)
          Interrupt:201

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:444298 (433.8 KiB)  TX bytes:444298 (433.8 KiB)
```


[CODE[COLOR="Red"]][root@SM01 /root][/COLOR]$ifconfig eth0 146.230.192.49
eth0: Link now 100-FullDuplex
[root@SM01 /root]$ping 146.230.193.109
PING 146.230.193.109 (146.230.193.109): 56 data bytes
64 bytes from 146.230.193.109: icmp_seq=0 ttl=64 time=0.7 ms
64 bytes from 146.230.193.109: icmp_seq=1 ttl=64 time=0.3 ms
64 bytes from 146.230.193.109: icmp_seq=2 ttl=64 time=0.3 ms

--- 146.230.193.109 ping statistics ---
3 packets transmitted, 3 packets received, 0% packet loss
round-trip min/avg/max = 0.3/0.4/0.7 ms
[root@SM01 /root]$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:60:6E:12:34:56
          inet addr:146.230.192.49  Bcast:146.230.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          Interrupt:24 Base address:0xc000[/CODE]

---

### Post by cinderella on 2006-10-18
> **mips said:**
> Found this, [http://www.linuxquestions.org/questions/showthread.php?t=59343](http://www.linuxquestions.org/questions/showthread.php?t=59343)

Do you have a firewall running on Ubuntu by any chance ?

what does ur /etc/hosts file look like???

mine looks like this:

```
127.0.0.1 localhost Bulletproof
127.0.1.1 Bulletproof

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Jus a thought, remember that thread that u referred me to inorder to re-install nfs-kernel-erver, portmap, nfs-common... well in that thread it said that there should not be a loop back but in this hosts file it seems to me as if there is a loop back. I will research this more and let u know

---

### Post by mips on 2006-10-19
> **cinderella said:**
> Jus a thought, remember that thread that u referred me to inorder to re-install nfs-kernel-erver, portmap, nfs-common... well in that thread it said that there should not be a loop back but in this hosts file it seems to me as if there is a loop back. I will research this more and let u know

No, you will have a loopback but you must not BIND portmap to it.

---

### Post by cinderella on 2006-10-19
thanks!!! 

But guess what I did???
```

[COLOR="Red"]bulletproof@Bulletproof:~$ grep set /etc/init.d/portmap [/COLOR]        sleep 1 # needs a short pause or pmap_set won't work. :(
          pmap_set </var/run/portmap.upgrade-state
            pmap_set </var/run/portmap.state
[COLOR="Red"]bulletproof@Bulletproof:~$ chmod -x /sbin/portmap[/COLOR]
chmod: changing permissions of `/sbin/portmap': Operation not permitted
[COLOR="Red"]bulletproof@Bulletproof:~$ sudo chmod -x /sbin/portmap[/COLOR]
[COLOR="Red"]bulletproof@Bulletproof:~$ sudo /etc/init.d/portmap restart[/COLOR]
  * Stopping portmap daemon...                                            [ ok ]
 * Starting portmap daemon... start-stop-daemon: Unable to start /sbin/portmap: Permission denied (Permission denied)
                                                                         [COLOR="SeaGreen"][fail][/COLOR]
```

now I get this:
```

ls: portmap.state: No such file or directory
bulletproof@Bulletproof:/$ cat portmap.state
cat: portmap.state: No such file or directory
bulletproof@Bulletproof:/$
```

Can u check what permissions u have set for your portmap???????

---

### Post by mips on 2006-10-19
[COLOR=Red]**-rwxr-xr-x**[/COLOR] 1 root root 14200 2006-01-13 10:44 portmap

---

### Post by cinderella on 2006-10-19
> **mips said:**
> No, you will have a loopback but you must not BIND portmap to it.

thanks!that makes logical sense!!! so far i have not made any break through but im still trying. i was busy during the day doing other stuff so hopefully i can solve this IRRITATING mount: rpc: timed out problem. wish me luck

---

### Post by cinderella on 2006-10-19
> **mips said:**
> [COLOR=Red]**-rwxr-xr-x**[/COLOR] 1 root root 14200 2006-01-13 10:44 portmap


gosh how the hell do i write a chmod for that!!!!!

---

### Post by cinderella on 2006-10-19
> **cinderella said:**
> gosh how the hell do i write a chmod for that!!!!!

how do go about checking if my firewall is activated/deactivated and if it is activated how do i deactivate it

---

### Post by pjbgravely on 2006-10-31
> **cinderella said:**
> hi i forgot how to use the vi editor!!!! i knew this 3 years ago

Make life easier on yourself, just use pico or nano instead.

I read this thread because I have the same problem also. In my case I changed from Edubuntu to Ubuntu server and all clients but 1 get the time out. I am going nuts. Since the clients didn't change but the server and network did, I have to assume it is the server or the network. If I am going to start a thread in the server section. If I figure it out I will let you know.

Paul

---

