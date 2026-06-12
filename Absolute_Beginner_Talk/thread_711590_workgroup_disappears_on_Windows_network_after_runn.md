---
title: "workgroup disappears on Windows network after running post-installation updates"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by ekendra on 2008-02-29
ok. I tried ubuntu back in 2005 and had too many issues with hardware to persevere.

a few friends convinced me that it was much improved in that department now. I thought I'd give it a go on my laptop while keeping Vista running on my desktop.

I installed Gutsy Gibbon yesterday. Beautiful! :guitar: 

Not a single hitch with hardware - and that's something that Windows can't brag about. Now I'm convinced to keep with Ubuntu and even recommend it to others.

Here's my issue: 

- when i first installed it - ubuntu  intuitively discovered my wireless network (via router - not adhoc)

- all i needed to give it was the passphrase and we were connected. i could even browse 'public' folders on my Vista box (albeit without write permissions) - so far so good.

- after downloading and running the package updates (as per the prompt thingy that flashes orange in the upper right panel) , i can no longer see the network locations. I go to 'Places -> Network' and there the icon for 'Windows Network' shows in the File Browser but when i navigate into the windows network none of my places are visible.

i don't have any access or even acknowledgment that these places exist. Can't even see the workgroup any more.

Could it be that Vista is just envious of my shiny new Ubuntu installation and all the attention I'm giving it and is having some sort of tantrum? :confused:


the other problem i had was that  'nm-applet' wants the default keyring every single time i boot up. (i did try various hacks that i found in the forums here and none of them really did the trick)

---

### Post by ekendra on 2008-02-29
results of: ifconfig

ekendra@Nitai:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:60:36:B6:CE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28013 (27.3 KB)  TX bytes:28013 (27.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:94:1F:71  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe94:1f71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7998 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13639320 (13.0 MB)  TX bytes:1072172 (1.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-09-5B-94-1F-71-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


---------------------- 

results of smbtree :

ekendra@Nitai:~$ smbtree
WORKGROUP
        \\GAURA          
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine GAURA.  Error was NT_STATUS_ACCESS_DENIED
MSHOME
        \\NITAI                         Nitai server (Samba, Ubuntu)
                \\NITAI\IPC$            IPC Service (Nitai server (Samba, Ubuntu))
                \\NITAI\print$          Printer Drivers
                \\NITAI\ekendra        
e

-----------------------

what is strange is that when I load the live CD i can network with the Vista Box 'GAURA'. Its just been since i ran the post-installation updates that I've had this issue.

---

### Post by ekendra on 2008-02-29
When I click on the windows network in the network file browser i get a message at the bottom stating that the icon is selected however, nothing happens.

---

### Post by ekendra on 2008-02-29
more results:

ekendra@Nitai:~$ smbclient -L 192.168.1.136
Password: 
Domain=[GAURA] OS=[Windows Vista (TM) Ultimate 6000] Server=[Windows Vista (TM) Ultimate 6.0]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        Canon Inkjet MP830 Series Printer   Canon Inkjet MP830 Series
        E               Disk      
        E$              Disk      Default share
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        Public          Disk      
        Send To OneNote 2007 Printer   Send To OneNote 2007
session request to 192.168.1.136 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

---

### Post by ekendra on 2008-02-29
more results:

ekendra@Nitai:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"gopal"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:16:38:C7:16:A1   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=79/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by herbster on 2008-02-29
The network disappearing from nautilus' file browser is a known bug, I posted quite a while ago about it as well. It can just stop showing the network and it doesn't come back. I don't know that it's been fixed, don't think it has :(

---

### Post by ekendra on 2008-02-29
thanks - but that only leads me to the obvious consideration that ubuntu doesnt' work properly yet.

great if someone could help me to troubleshoot here. I've posted probably too much data - I'm hopeful that someone can make sense of it and tell me what I need to do to get my network functional again. i need to work with this network - its mission critical. If I can't get this happening by say Monday I'll need to reinstall XP on this laptop.

Shame - so close.

---

### Post by herbster on 2008-03-01
Okay, before I post commands and stuff that may not be useful-- I'm assuming you just want to have your network shares mounted, so you can browse them and transfer files to and from, right? ie., Open a Windows share on your other computer in a file browser and do what you need with folders/files.

---

### Post by ekendra on 2008-03-01
yup. that's pretty much it. i want to sit here on my cool new Ubuntu machine and be able to copy, move and delete files on my windows vista box. I also want to be able to move files off my vista and onto the ubuntu system.

it'd be nice if i could still do this all vice-versa too but i think that's easier (already got that working with Samba)

---

### Post by herbster on 2008-03-01
That's pretty much what I do with my XP box in another room. This should work:

First make a directory you'd like to mount the share to, let's say vistashare:

```
sudo mkdir /media/vistashare
```

Now backup fstab:

```
sudo cp /etc/fstab /etc/fstab.backup
```

Now open for editing:

```
sudo gedit /etc/fstab
```

Paste this line at the very end on a new line:

```
//192.168.1.XXX/yourvistasharedfolder /media/vistashare cifs user=username,pass=password
```

192.168.1.XXX = IP of your Vista box. For instance my linux box is 192.168.1.1, my XP box is 192.168.1.105. Find yours out-- easily done in Vista by hitting Start > typing "cmd" and hit ENTER > type ipconfig and hit ENTER, look for the IPv4 address.

user and pass are pretty straightforward, just replace "username" and "password" with the user/pass you have on your Vista box. If you don't use any login on the Vista machine, just omit that part.

Hope it helps.

---

### Post by ekendra on 2008-03-01
hey! that worked! not sure what I did but whatever. hopefully i'll pick this stuff up on day.

thanks heaps! 

go-run-gaa-!!

---

### Post by ekendra on 2008-03-02
well.. it worked great until i restarted my machine. now we're back to square one it seems. tried to follow the instructions again but it didn't seem to fix anything.

any other suggestions?

---

### Post by stormzen on 2008-03-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/198002](https://bugs.launchpad.net/ubuntu/+bug/198002) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've got a suggestion.

"I went back to my original installed file. It appears that commenting out both the "interface" settings and the "host allow" settings causes both Nautilus and Konqueror to work as expected. ... Unless Samba is doing away with those settings, however, it's probably still a bug."

( See bug report that I filed on this, below; Please add any details that you see fit to that report. )  This anomoly has appeared to plague various users of the samba for a year now; let's do what we can to get it fixed.

---

### Post by stormzen on 2008-03-03
Incidentally, if that does fix the problem, *do* make sure that your firewall doesn't allow SMB packets across the network.  ( Windows SMB is a wide-open and chatty protocol. )

---

### Post by herbster on 2008-03-03
ekendra,

```
cat /etc/fstab
```

Paste output.

---

### Post by ekendra on 2008-03-03
here's how i finally got this working. 

- I went to 'Places -> Connect to Server ...'
- I set the 'Service type:' to 'Windows share'
- I typed in the IP address of my Windows Vista box in the 'Server' field
- closed that screen
- Now a folder launcher appears on my desktop and under 'Places' with the IP address as a title. I can navigate all my shared windows folders through there.

hope this helps someone.

---

### Post by herbster on 2008-03-03
Glad you got it working, yes that solution is fine if you use nautilus. Can you still paste your /etc/fstab so I can see what went wrong? I've been using my solution for a while and it has never failed, I'm curious what caused it to not renew on reboot...

---

### Post by ekendra on 2008-03-03
sure bro:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=064a6855-26f2-43cc-a08f-639147764eb1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a0bbf995-3bc1-4233-b20c-e66477ce25a7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
//192.168.1.136/E /media/vistashare cifs

---

### Post by herbster on 2008-03-03
```
sudo mount -a
```

Do that and then try opening the vistashare folder, see if it's now mounted.

---

