---
title: "What makes linux secure"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by lamar_air on 2007-07-26
Why is Linux more secure from network attacks?  I mean attacks that can be carried out directly over a network and don't require the user to run, install, or allow a script to run in a priveleged area on their OS.

I know there're currently aren't as many virus's that are targeted towards Linux but aside from that what are the fundamental design differences that make Windows so vulnerable to these attacks and Linux not so vulnerable?

---

### Post by marco123 on 2007-07-26
Firstly Ubuntu ships with no open ports so hackers can't connect to a Ubuntu box.

Secondly no changes can be made to the system without the password, so you would have to give your permission and password every step of the way for a virus to install and make system changes.

Linux was built with networking in mind unlike windows.

---

### Post by Ek0nomik on 2007-07-26
File permissions and the simple fact that Linux isn't as popular as Windows.

Those would be my top two.

---

### Post by lamar_air on 2007-07-26
Marco123 what about port 80?  The blaster worm exploited that port and caused a DoS.  How does Linux prevent that type of attack for example?

---

### Post by sad_iq on 2007-07-26
Well linux (Ubuntu in our case) is more secure over network attacks firstly because it has no open ports to the outside...so no script can attack any vulnerable program(No Open Ports=Nothing To Target). Also any program that can be exploited usually will be patched way sooner(sometimes in just hours)than it would happen in a windows environent and the exploit would be useless on a linux machine!!!
 Also because the source code is opened to everyone there are people allways trying to find flaws and fix it before an exploit can cause damage. In an windows environment patching has to be done by microsoft's staff and takes ages to patch, leaving the users with an unsecure station, and with many services opened to the outside world(by default)!!!

---

### Post by Nekiruhs on 2007-07-26
> **lamar_air said:**
> Marco123 what about port 80?  The blaster worm exploited that port and caused a DoS.  How does Linux prevent that type of attack for example?
Not even port 80 is open by default. All ports are stealth on a default ubuntu install. Sheilds up confirms this.

---

### Post by aysiu on 2007-07-26
Are we talking about Linux on the server or Linux on the desktop/laptop?

---

### Post by Zzl1xndd on 2007-07-26
> **Ek0nomik said:**
> the simple fact that Linux isn't as popular as Windows.


I know people always say this but I don't think it has much to do with it. Linux is not overly popular on the Desktop but that is not the case with servers and a Server is often a more attractive target then a home user (at least it was in the past before Zombies and those zombies are used to attack servers). So in such a case you would think that Linux would have a large number of exploits but still it doesn't.

---

### Post by asmoore82 on 2007-07-26
IN MY EXPERIENCE ... years ago ... in the days of Windows 2000 Pro and Red Hat Linux 7.3 (valhalla)

1. Windows blind stab at security seems to revolve around cowering in corners. Windows machines do not respond to blind Network pings and as such a simple ping scan of a network will not detect windows machines. Linux machines, however, will show up in the same simple scan.
But, doing broadcast scans on multiple ports easily detects Windows machines right along with the Linux machines. Now we are at a level playing field and windows's first line of defense has been compromised.

2. In order for ANYTHING to affect a system network security wise, there must be open ports on that system, Linux out of the box has NO open ports by default. Windows on the other hand, has TCP ports open for Windows File Sharing _EVEN_ IF NOTHING IS SHARED. The conversation on Windows security cannont go further because the machine is already Doomed. Moving on with Linux.

3. after out-of-the-box setup, ports may be open on Linux, but they will always have a stable service program behind those ports. AND back in the day, there was a rock solid wrapper service around all misc. open ports called 'xinetd' that had to okay traffic BEFORE passing it on to those service programs with few acceptions such as OpenSSH login server on port 22 and apache web server on port 80. FTP servers commonly came with dual modes, one to run within xinetd framework and another to run standalone. That ssh server on port 22 will accept data from any Tom/Dick/Harry but they can't do a darn thing without first providing a valid username/password for the local machine.

here is a port scan of my Ubuntu 7.04 laptop right now, after manually enabling ssh
```
asmoore@asmoore-laptop:~$ nmap -v $HOSTNAME

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-26 11:18 EDT
Initiating Connect() Scan at 11:18
Scanning asmoore-laptop (127.0.1.1) [1697 ports]
Discovered open port 22/tcp on 127.0.1.1
Completed Connect() Scan at 11:18, 0.03s elapsed (1697 total ports)
[b]Host asmoore-laptop (127.0.1.1) appears to be up ... good.
Interesting ports on asmoore-laptop (127.0.1.1):
Not shown: 1696 closed ports
PORT   STATE SERVICE
22/tcp open  ssh[/b]

Nmap finished: 1 IP address (1 host up) scanned in 0.171 seconds
```
^^ nothing Open but what I say is to be open.

here is a scan of the nearest Windows Box.
```
asmoore@asmoore-laptop:~$ nmap -v 10.200.1.194

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-26 11:20 EDT
Machine 10.200.1.194 MIGHT actually be listening on probe port 80
Initiating Parallel DNS resolution of 1 host. at 11:20
Completed Parallel DNS resolution of 1 host. at 11:20, 0.00s elapsed
Initiating Connect() Scan at 11:20
Scanning 10.200.1.194 [1697 ports]
Discovered open port 80/tcp on 10.200.1.194
Discovered open port 3389/tcp on 10.200.1.194
Discovered open port 135/tcp on 10.200.1.194
Discovered open port 5800/tcp on 10.200.1.194
Discovered open port 139/tcp on 10.200.1.194
Discovered open port 1025/tcp on 10.200.1.194
Discovered open port 445/tcp on 10.200.1.194
Discovered open port 5900/tcp on 10.200.1.194
Completed Connect() Scan at 11:20, 1.31s elapsed (1697 total ports)
[b]Host 10.200.1.194 appears to be up ... good.
Interesting ports on 10.200.1.194:
Not shown: 1689 closed ports
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1025/tcp open  NFS-or-IIS
3389/tcp open  ms-term-serv
5800/tcp open  vnc-http
5900/tcp open  vnc[/b]

Nmap finished: 1 IP address (1 host up) scanned in 1.428 seconds
```
^^ pick-a-port any port and attack

Next Move? Aggressive scans with root permission...
```
asmoore@asmoore-laptop:~$ sudo nmap -v -A $HOSTNAME

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-26 11:25 EDT
Initiating SYN Stealth Scan at 11:25
Scanning asmoore-laptop (127.0.1.1) [1697 ports]
Discovered open port 22/tcp on 127.0.1.1
Completed SYN Stealth Scan at 11:26, 22.49s elapsed (1697 total ports)
Initiating Service scan at 11:26
Scanning 1 service on asmoore-laptop (127.0.1.1)
Completed Service scan at 11:26, 0.01s elapsed (1 service on 1 host)
**Warning:  OS detection for 127.0.1.1 will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port**
Initiating OS detection (try #1) against asmoore-laptop (127.0.1.1)
Retrying OS detection (try #2) against asmoore-laptop (127.0.1.1)
Initiating gen1 OS Detection against 127.0.1.1 at 26.997s
**Warning:  OS detection will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port**
For OSScan assuming port 22 is open, 44432 is closed, and neither are firewalled
For OSScan assuming port 22 is open, 43384 is closed, and neither are firewalled
For OSScan assuming port 22 is open, 41445 is closed, and neither are firewalled
[b]Host asmoore-laptop (127.0.1.1) appears to be up ... good.
Interesting ports on asmoore-laptop (127.0.1.1):
Not shown: 1696 filtered ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 4.3p2 Debian 8ubuntu1 (protocol 2.0)
Device type: general purpose|WAP
Running (JUST GUESSING) : Linux 2.6.X (95%), Siemens linux (90%)
Aggressive OS guesses: Linux 2.6.17-10.33 (Ubuntu) (95%)[/b], Linux 2.6.14 - 2.6.17 (90%), Linux 2.6.17 - 2.6.18 (x86) (90%), Linux 2.6.17.8 (x86) (90%), Linux 2.6.18 - 2.6.19 (x86) (90%), Siemens Gigaset SE515dsl wireless broadband router (90%), Linux 2.6.14 - 2.6.16 (90%), Linux 2.6.17 (x86) (90%), Linux 2.6.17 - 2.6.18 (89%), Linux 2.6.18.2 (x86) (89%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=0 (Trivial joke)
IPID Sequence Generation: All zeros
Service Info: OS: Linux

OS and Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 36.154 seconds
               Raw packets sent: 3528 (160.284KB) | Rcvd: 50 (4376B)
**asmoore@asmoore-laptop:~$** sudo nmap -v -A 10.200.1.194

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-26 11:27 EDT
Initiating ARP Ping Scan at 11:27
Scanning 10.200.1.194 [1 port]
Completed ARP Ping Scan at 11:27, 0.02s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:27
Completed Parallel DNS resolution of 1 host. at 11:27, 0.00s elapsed
Initiating SYN Stealth Scan at 11:27
Scanning 10.200.1.194 [1697 ports]
Discovered open port 80/tcp on 10.200.1.194
Discovered open port 3389/tcp on 10.200.1.194
Discovered open port 135/tcp on 10.200.1.194
Discovered open port 5800/tcp on 10.200.1.194
Discovered open port 445/tcp on 10.200.1.194
Discovered open port 5900/tcp on 10.200.1.194
Discovered open port 139/tcp on 10.200.1.194
Discovered open port 1025/tcp on 10.200.1.194
Completed SYN Stealth Scan at 11:27, 1.36s elapsed (1697 total ports)
Initiating Service scan at 11:27
Scanning 8 services on 10.200.1.194
Completed Service scan at 11:27, 6.40s elapsed (8 services on 1 host)
Initiating OS detection (try #1) against 10.200.1.194
Retrying OS detection (try #2) against 10.200.1.194
Retrying OS detection (try #3) against 10.200.1.194
Retrying OS detection (try #4) against 10.200.1.194
Retrying OS detection (try #5) against 10.200.1.194
[b]Host 10.200.1.194 appears to be up ... good.
Interesting ports on 10.200.1.194:
Not shown: 1689 closed ports
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft IIS webserver 6.0
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds  Microsoft Windows 2003 microsoft-ds
1025/tcp open  msrpc         Microsoft Windows RPC
3389/tcp open  microsoft-rdp Microsoft Terminal Service
5800/tcp open  vnc-http      Ultr@VNC (Resolution 800x632; VNC TCP port: 5900)
5900/tcp open  vnc           VNC (protocol 3.6)
MAC Address: 00:D0:B7:B0:B2:B1 (Intel)
No exact OS matches for host (If you know what OS is running on it, see http://insecure.org/nmap/submit/ ).[/b]
TCP/IP fingerprint:
OS:SCAN(V=4.20%D=7/26%OT=80%CT=1%CU=41326%PV=Y%DS=1%G=Y%M=00D0B7%TM=46A8BD6
OS:C%P=i686-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=107%TI=I%II=I%SS=S%TS=0)SEQ(S
OS:P=104%GCD=1%ISR=107%TI=I%II=I%SS=S%TS=0)SEQ(SP=105%GCD=1%ISR=107%TI=I%II
OS:=I%SS=S%TS=0)OPS(O1=M5B4NW0NNT00NNS%O2=M5B4NW0NNT00NNS%O3=M5B4NW0NNT00%O
OS:4=M5B4NW0NNT00NNS%O5=M5B4NW0NNT00NNS%O6=M5B4NNT00NNS)WIN(W1=4000%W2=4000
OS:%W3=4000%W4=4000%W5=4000%W6=4000)ECN(R=Y%DF=N%T=80%W=4000%O=M5B4NW0NNS%C
OS:C=N%Q=)T1(R=Y%DF=N%T=80%S=O%A=S+%F=AS%RD=0%Q=)T2(R=Y%DF=N%T=80%W=0%S=Z%A
OS:=S%F=AR%O=%RD=0%Q=)T3(R=Y%DF=N%T=80%W=4000%S=O%A=S+%F=AS%O=M5B4NW0NNT00N
OS:NS%RD=0%Q=)T4(R=Y%DF=N%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T5(R=Y%DF=N%T=80%
OS:W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=N%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=
OS:)T7(R=Y%DF=N%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=80%TOS=0%IP
OS:L=B0%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUL=G%RUD=G)IE(R=Y%DFI=S%T=80%TOSI
OS:=Z%CD=Z%SI=S%DLI=S)


Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IPID Sequence Generation: Incremental
Service Info: OS: Windows

OS and Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 18.311 seconds
               Raw packets sent: 1876 (86.112KB) | Rcvd: 1779 (84.276KB)
```

---

### Post by sad_iq on 2007-07-26
> **lamar_air said:**
> Marco123 what about port 80?  The blaster worm exploited that port and caused a DoS.  How does Linux prevent that type of attack for example?
 AAA...how does this sound: "The Blaster Worm (also known as Lovsan or Lovesan) was a computer worm that spread on computers running the Microsoft operating systems, Windows XP and Windows 2000, during August 2003" - wikipedia
 Also you can rest assured that this exploit would not be able to infect any system(windows or linux) at the present date! Besides...there are many ways to set up a server in linux that would prevent an attack to take over the whole system(chroot sounds good)...so even if a program would be compromised, then it could be temporarily stopped until a patch would be submitted.
 A DoS (Denial Of Service) will be devastating on a home connection...there are little ways you can prevent or survive a (not to) large ping flood attack(or any type of attacks...again...on a normal home link)!!

---

### Post by lamar_air on 2007-07-26
Thanks a lot for the replies everyone but i'd like to get a bit better understanding on the closed port idea.  By default port 80 is closed but then say you use your web browser to access the internet through that port even though it's closed can you still access the internet?  Or does it then become opened for some period of time?

---

### Post by asmoore82 on 2007-07-26
i've explained that within the last few days.... found it!

[http://ubuntuforums.org/showthread.php?p=3076032#post3076032](http://ubuntuforums.org/showthread.php?p=3076032#post3076032)

---

### Post by sad_iq on 2007-07-26
The opened ports thing is that is has to be a listening program that opens them...that means a program that will accept incoming connections...when you browse the internet firefox opens a port but does not accept connections. If a program doesn't open a port and accepts incoming connections it cannot be targeted by network remote exploits...it has to be a different type of exploit(like tricking you into visiting some site). So unless you specifically install a server app(like apache,ssh, or whatever) you will be safe from remote exploits, and if you are behind a router it will have a firewall blocking external connections,so even if you install apache you would have to manually configure your router to let all requests get to your system(witch will never happen accidentaly ). Result...**your linux box is secure** (unless you really don't know what you're doing!!!)

---

### Post by marco123 on 2007-07-26
> **asmoore82 said:**
> IN MY EXPERIENCE ... years ago ... in the days of Windows 2000 Pro and Red Hat Linux 7.3 (valhalla)

1. Windows blind stab at security seems to revolve around cowering in corners. Windows machines do not respond to blind Network pings and as such a simple ping scan of a network will not detect windows machines. Linux machines, however, will show up in the same simple scan.
But, doing broadcast scans on multiple ports easily detects Windows machines right along with the Linux machines. Now we are at a level playing field and windows's first line of defense has been compromised.

2. In order for ANYTHING to affect a system network security wise, there must be open ports on that system, Linux out of the box has NO open ports by default. Windows on the other hand, has TCP ports open for Windows File Sharing _EVEN_ IF NOTHING IS SHARED. The conversation on Windows security cannont go further because the machine is already Doomed. Moving on with Linux.

3. after out-of-the-box setup, ports may be open on Linux, but they will always have a stable service program behind those ports. AND back in the day, there was a rock solid wrapper service around all misc. open ports called 'xinetd' that had to okay traffic BEFORE passing it on to those service programs with few acceptions such as OpenSSH login server on port 22 and apache web server on port 80. FTP servers commonly came with dual modes, one to run within xinetd framework and another to run standalone. That ssh server on port 22 will accept data from any Tom/Dick/Harry but they can't do a darn thing without first providing a valid username/password for the local machine.

here is a port scan of my Ubuntu 7.04 laptop right now, after manually enabling ssh
```
asmoore@asmoore-laptop:~$ nmap -v $HOSTNAME

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-26 11:18 EDT
Initiating Connect() Scan at 11:18
Scanning asmoore-laptop (127.0.1.1) [1697 ports]
Discovered open port 22/tcp on 127.0.1.1
Completed Connect() Scan at 11:18, 0.03s elapsed (1697 total ports)
[b]Host asmoore-laptop (127.0.1.1) appears to be up ... good.
Interesting ports on asmoore-laptop (127.0.1.1):
Not shown: 1696 closed ports
PORT   STATE SERVICE
22/tcp open  ssh[/b]

Nmap finished: 1 IP address (1 host up) scanned in 0.171 seconds
```
^^ nothing Open but what I say is to be open.

here is a scan of the nearest Windows Box.
```
asmoore@asmoore-laptop:~$ nmap -v 10.200.1.194

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-26 11:20 EDT
Machine 10.200.1.194 MIGHT actually be listening on probe port 80
Initiating Parallel DNS resolution of 1 host. at 11:20
Completed Parallel DNS resolution of 1 host. at 11:20, 0.00s elapsed
Initiating Connect() Scan at 11:20
Scanning 10.200.1.194 [1697 ports]
Discovered open port 80/tcp on 10.200.1.194
Discovered open port 3389/tcp on 10.200.1.194
Discovered open port 135/tcp on 10.200.1.194
Discovered open port 5800/tcp on 10.200.1.194
Discovered open port 139/tcp on 10.200.1.194
Discovered open port 1025/tcp on 10.200.1.194
Discovered open port 445/tcp on 10.200.1.194
Discovered open port 5900/tcp on 10.200.1.194
Completed Connect() Scan at 11:20, 1.31s elapsed (1697 total ports)
[b]Host 10.200.1.194 appears to be up ... good.
Interesting ports on 10.200.1.194:
Not shown: 1689 closed ports
PORT     STATE SERVICE
80/tcp   open  http
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1025/tcp open  NFS-or-IIS
3389/tcp open  ms-term-serv
5800/tcp open  vnc-http
5900/tcp open  vnc[/b]

Nmap finished: 1 IP address (1 host up) scanned in 1.428 seconds
```
^^ pick-a-port any port and attack

Next Move? Aggressive scans with root permission...
```
asmoore@asmoore-laptop:~$ sudo nmap -v -A $HOSTNAME

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-26 11:25 EDT
Initiating SYN Stealth Scan at 11:25
Scanning asmoore-laptop (127.0.1.1) [1697 ports]
Discovered open port 22/tcp on 127.0.1.1
Completed SYN Stealth Scan at 11:26, 22.49s elapsed (1697 total ports)
Initiating Service scan at 11:26
Scanning 1 service on asmoore-laptop (127.0.1.1)
Completed Service scan at 11:26, 0.01s elapsed (1 service on 1 host)
**Warning:  OS detection for 127.0.1.1 will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port**
Initiating OS detection (try #1) against asmoore-laptop (127.0.1.1)
Retrying OS detection (try #2) against asmoore-laptop (127.0.1.1)
Initiating gen1 OS Detection against 127.0.1.1 at 26.997s
**Warning:  OS detection will be MUCH less reliable because we did not find at least 1 open and 1 closed TCP port**
For OSScan assuming port 22 is open, 44432 is closed, and neither are firewalled
For OSScan assuming port 22 is open, 43384 is closed, and neither are firewalled
For OSScan assuming port 22 is open, 41445 is closed, and neither are firewalled
[b]Host asmoore-laptop (127.0.1.1) appears to be up ... good.
Interesting ports on asmoore-laptop (127.0.1.1):
Not shown: 1696 filtered ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 4.3p2 Debian 8ubuntu1 (protocol 2.0)
Device type: general purpose|WAP
Running (JUST GUESSING) : Linux 2.6.X (95%), Siemens linux (90%)
Aggressive OS guesses: Linux 2.6.17-10.33 (Ubuntu) (95%)[/b], Linux 2.6.14 - 2.6.17 (90%), Linux 2.6.17 - 2.6.18 (x86) (90%), Linux 2.6.17.8 (x86) (90%), Linux 2.6.18 - 2.6.19 (x86) (90%), Siemens Gigaset SE515dsl wireless broadband router (90%), Linux 2.6.14 - 2.6.16 (90%), Linux 2.6.17 (x86) (90%), Linux 2.6.17 - 2.6.18 (89%), Linux 2.6.18.2 (x86) (89%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 0 hops
TCP Sequence Prediction: Difficulty=0 (Trivial joke)
IPID Sequence Generation: All zeros
Service Info: OS: Linux

OS and Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 36.154 seconds
               Raw packets sent: 3528 (160.284KB) | Rcvd: 50 (4376B)
**asmoore@asmoore-laptop:~$** sudo nmap -v -A 10.200.1.194

Starting Nmap 4.20 ( http://insecure.org ) at 2007-07-26 11:27 EDT
Initiating ARP Ping Scan at 11:27
Scanning 10.200.1.194 [1 port]
Completed ARP Ping Scan at 11:27, 0.02s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 11:27
Completed Parallel DNS resolution of 1 host. at 11:27, 0.00s elapsed
Initiating SYN Stealth Scan at 11:27
Scanning 10.200.1.194 [1697 ports]
Discovered open port 80/tcp on 10.200.1.194
Discovered open port 3389/tcp on 10.200.1.194
Discovered open port 135/tcp on 10.200.1.194
Discovered open port 5800/tcp on 10.200.1.194
Discovered open port 445/tcp on 10.200.1.194
Discovered open port 5900/tcp on 10.200.1.194
Discovered open port 139/tcp on 10.200.1.194
Discovered open port 1025/tcp on 10.200.1.194
Completed SYN Stealth Scan at 11:27, 1.36s elapsed (1697 total ports)
Initiating Service scan at 11:27
Scanning 8 services on 10.200.1.194
Completed Service scan at 11:27, 6.40s elapsed (8 services on 1 host)
Initiating OS detection (try #1) against 10.200.1.194
Retrying OS detection (try #2) against 10.200.1.194
Retrying OS detection (try #3) against 10.200.1.194
Retrying OS detection (try #4) against 10.200.1.194
Retrying OS detection (try #5) against 10.200.1.194
[b]Host 10.200.1.194 appears to be up ... good.
Interesting ports on 10.200.1.194:
Not shown: 1689 closed ports
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft IIS webserver 6.0
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds  Microsoft Windows 2003 microsoft-ds
1025/tcp open  msrpc         Microsoft Windows RPC
3389/tcp open  microsoft-rdp Microsoft Terminal Service
5800/tcp open  vnc-http      Ultr@VNC (Resolution 800x632; VNC TCP port: 5900)
5900/tcp open  vnc           VNC (protocol 3.6)
MAC Address: 00:D0:B7:B0:B2:B1 (Intel)
No exact OS matches for host (If you know what OS is running on it, see http://insecure.org/nmap/submit/ ).[/b]
TCP/IP fingerprint:
OS:SCAN(V=4.20%D=7/26%OT=80%CT=1%CU=41326%PV=Y%DS=1%G=Y%M=00D0B7%TM=46A8BD6
OS:C%P=i686-pc-linux-gnu)SEQ(SP=105%GCD=1%ISR=107%TI=I%II=I%SS=S%TS=0)SEQ(S
OS:P=104%GCD=1%ISR=107%TI=I%II=I%SS=S%TS=0)SEQ(SP=105%GCD=1%ISR=107%TI=I%II
OS:=I%SS=S%TS=0)OPS(O1=M5B4NW0NNT00NNS%O2=M5B4NW0NNT00NNS%O3=M5B4NW0NNT00%O
OS:4=M5B4NW0NNT00NNS%O5=M5B4NW0NNT00NNS%O6=M5B4NNT00NNS)WIN(W1=4000%W2=4000
OS:%W3=4000%W4=4000%W5=4000%W6=4000)ECN(R=Y%DF=N%T=80%W=4000%O=M5B4NW0NNS%C
OS:C=N%Q=)T1(R=Y%DF=N%T=80%S=O%A=S+%F=AS%RD=0%Q=)T2(R=Y%DF=N%T=80%W=0%S=Z%A
OS:=S%F=AR%O=%RD=0%Q=)T3(R=Y%DF=N%T=80%W=4000%S=O%A=S+%F=AS%O=M5B4NW0NNT00N
OS:NS%RD=0%Q=)T4(R=Y%DF=N%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=)T5(R=Y%DF=N%T=80%
OS:W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=N%T=80%W=0%S=A%A=O%F=R%O=%RD=0%Q=
OS:)T7(R=Y%DF=N%T=80%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(R=Y%DF=N%T=80%TOS=0%IP
OS:L=B0%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUL=G%RUD=G)IE(R=Y%DFI=S%T=80%TOSI
OS:=Z%CD=Z%SI=S%DLI=S)


Network Distance: 1 hop
TCP Sequence Prediction: Difficulty=261 (Good luck!)
IPID Sequence Generation: Incremental
Service Info: OS: Windows

OS and Service detection performed. Please report any incorrect results at http://insecure.org/nmap/submit/ .
Nmap finished: 1 IP address (1 host up) scanned in 18.311 seconds
               Raw packets sent: 1876 (86.112KB) | Rcvd: 1779 (84.276KB)
```

Wow, wish I could have explained it that well. :)

---

### Post by lamar_air on 2007-07-26
The IP packet you send contains the port that you are requesting a response back to though so if someone see's your packet then they know what port you have open.  What's used to prevent them from carrying out an attack on that port then, say a DoS attack?

---

### Post by eentonig on 2007-07-26
> **lamar_air said:**
> Thanks a lot for the replies everyone but i'd like to get a bit better understanding on the closed port idea.  By default port 80 is closed but then say you use your web browser to access the internet through that port even though it's closed can you still access the internet?  Or does it then become opened for some period of time?

When you browse the internet. Packets travel from your pc to a server. Those packets are build like this:

<source IP address=your PC> + <source Port (random, say 85647)>; <destination IP address=webserver> + <destination Port (well known service=80)>

Which translates into

Someone/Some Program <source Port> at the address <source IP address> wants to talk to Mr Webserver (<destination Port> = 80) who lives at <destination IP address>.

If Mr Webserver wants to answer, he answers to the program and IP that were the sources in what he received. They become the destinations in his packet. And the sources become destination.


<source IP address=webserver> + <source Port (well known service=80)>;<destination IP address=your PC> + <destination Port (random, say 85647)>

Your PC receives this packet <destination IP address=your PC>, looks up the destination prgram <destination Port (random, say 85647)>. The Webbrowser screams from his room "Yeah, I was waiting for that. Sent him in!". and you get to see the webpage.

Now, let's say I want to play bad guy.
1. Case I:
I want you to be webserver:
<source IP address=Bad Guy> + <source Port (random, say 85647)>; <destination IP address=your PC> + <destination Port (well known service=80)>

Your Mr Linux opens the door, checks who the message is for and says "Nope, Mr Webserver doesn't live here. Bye now."

2. Case II:
Do I even have to explain what happens when somebody knocks on the door and says. "Hey, I got a packet for <quickly find out some random name>. Do you think anybody in his right mind will let that guy enter the building? Then why should your pc do so?

---

### Post by sad_iq on 2007-07-26
I think that (let's say firefox) won't accept connections...it is not a server, and as asmoore82 said on his link it's not firefox that changes ports, it's the server accepting connections on a different port, so the danger is for the server not us(firefox).Shouldn't the attacker know what port firefox will open to sniff the packet??? Also if the connection is encrypted...the ip packet cannot be sniffed(could be wrong on the last 2 statements)

---

### Post by lamar_air on 2007-07-26
So from eentonig's message Case I and Case II messages cannot come quick enough to cause a DoS on your machine by sending faster than you can process?  I guess TCP/IP messages would be much slower than your local machine's processing power.

Sad_iq, in many cases the frames are not encrypted because they must be quickly readable by routers.

---

### Post by sad_iq on 2007-07-26
> **lamar_air said:**
> 
Sad_iq, in many cases the frames are not encrypted because they must be quickly readable by routers.
So the initial handshake done by the source and the address is not encrypted??' Any way you can protect it from sniffing?? A spoof cannot be done ... wright???

---

### Post by asmoore82 on 2007-07-26
if you are talking about an encrypted connection the server and client exchange hidden plain text encryption keys then start sending every thing encrypted... a spoof cannont be done unless the spoofer has both private keys from the beginning  and the apps really watch out for this....

```
asmoore@asmoore-laptop:~$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 82:27:84:5f:d0:3b:17:4b:6b:f8:80:96:ec:b5:6d:f4.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
asmoore@localhost's password: 
Linux asmoore-laptop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Wed Jul 25 08:15:50 2007
asmoore@asmoore-laptop:~$ exit
logout
Connection to localhost closed.
asmoore@asmoore-laptop:~$ vi .ssh/known_hosts
< i changed one character in the file from lowercase to uppercase >
asmoore@asmoore-laptop:~$ ssh localhost
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
82:27:84:5f:d0:3b:17:4b:6b:f8:80:96:ec:b5:6d:f4.
Please contact your system administrator.
Add correct host key in /home/asmoore/.ssh/known_hosts to get rid of this message.
Offending key in /home/asmoore/.ssh/known_hosts:4
RSA host key for localhost has changed and you have requested strict checking.
Host key verification failed.
```

---

### Post by lamar_air on 2007-07-26
From what I understand, you're TCP/IP messages are NOT encrypted unless encryption is being done with hardware or by your application layer.  For the most part your IP and Port are free for others to see.

TCP Frame: [http://www.skullbox.net/diagrams/tcppacket.gif](http://www.skullbox.net/diagrams/tcppacket.gif) 
UDP Frame: [http://www.skullbox.net/diagrams/udppacket.gif](http://www.skullbox.net/diagrams/udppacket.gif) 
IP Frame: [http://www.netguru.net/courses/ntc/ntcgrap/Image53.gif](http://www.netguru.net/courses/ntc/ntcgrap/Image53.gif)

Can someone confirm...

---

### Post by bodhi.zazen on 2007-07-26
1. People make Linux secure. The OS is designed very differently then say Windows, as you can see above. Security and convenience are often competing factors and Windows was designed from day 1 to be convenient at the expense of security. To this effect many "holes" in the OS remain and Windows remains vulnerable and must be "hardened" by the addition of a router (most of which actually run *nix), firewall, anti virus, and anti-spyware ... all of which *should* have been built into the OS in the first place. Anyone who claims "never to have had a problem" with windows either has added the above applications or, in the event they have not, does not know how to check their system for breaches. 

2. If you want to have a secure system you will need to learn about how your OS works and how to ***maintain*** your security.

FYI I am working on an Ubuntu Security How-to and anticipate posting it in the Security and Servers section in the next few days (a draft document is under review now).

---

