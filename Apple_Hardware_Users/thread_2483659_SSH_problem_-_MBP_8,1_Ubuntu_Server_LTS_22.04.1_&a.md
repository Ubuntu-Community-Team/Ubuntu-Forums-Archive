---
title: "SSH problem - MBP 8,1 Ubuntu Server LTS 22.04.1 &amp; M2 MBP Ventura 13.2 Beta(22D49)"
date: 2023-02-05
forum: Apple Hardware Users
---

### Post by muzzmelbourne on 2023-02-05
Hi,

Newbie to Ubuntu Server, but 'nerding' around electronics/computers since 1975.

I have a 2011 13" 8,1 MBP 16Gb RAM, 500Gb SSD running Ubuntu Server 22.04.1 on ethernet. Runs like a charm, no issues. I also have a 2021 M2 MBP running Ventura 13.2(22D49). It runs like a charm, no issues.

I recently had the 8,1 MBP running Linux Mint(cinnamon) in Virtual Box 7.0 on MacOS Monterey 12.6 on top of OCLP 0.6.1 with no issues, other than speed. I am, therefore, confident it can handle dedicated text based server functions.

Ok, the problem,

I can establish an SSH connection between the machines(i.e. I have the remote machine prompt to login), but, when I enter the login password, I get either "access denied", "connection failed", "incorrect login - try again" or some variation of this.

[COLOR=#1A1A1A][FONT=Menlo]Last login: Sun Feb  5 23:49:03 on console[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo]murrayxxxxx@M2-MacBook-Pro-13 ~ % ssh esn/murray@xxx.xxx.x.xxx[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo](esn/murray@xxx.xxx.x.xxx) Password:[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo](esn/murray@xxx.xxx.x.xxx) Password:[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo](esn/murray@xxx.xxx.x.xxx) Password:[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo]esn/murray@xxx.xxx.x.xxx's password: [/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo]Permission denied, please try again.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo]esn/murray@xxx.xxx.x.xxx's password: [/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo]Received disconnect from xxx.xxx.x.xxx port 22:2: Too many authentication failures[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo]Disconnected from xxx.xxx.x.xxx port 22[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Menlo]murrayxxxxx@M2-MacBook-Pro-13 ~ %[/FONT][/COLOR]

As I said, I can connect the machines to each other, just can't login.

FYI, same modem, TP Link Archer300, latest firmware. Server via ethernet, client via WiFi. SSH keys are fresh and in the default locations. Fingerprints have been exchanged and recorded.

I have completely reinstalled Ubuntu on the server MBP 4 times from USB iso paying particular attention to system/user names and passwords. It runs smoothly

Any ideas folks? I'm flummoxed.

Cheers.


UPDATE: Solved!

I have Tabby, a CLI app, that I played with 3 months ago but did nothing with really. 

Turns out, I setup a 'profile' in it for an old company I ran, that I was unaware of. Seems this Tabby controls ALL command line interactions, including the system CLI, even when its not running. So, every time I went to SSH to my current setup it was implementing an irrelevant set of login rules, which barred password logins. A quick 'profile' delete and a new one created and, bazinga, I was 'in'. Did a remote system reboot to check operations and all good. 

Totally stumbled across this problem/solution via accidental keystrokes at the command line.

Cheers

---

### Post by TheFu on 2023-02-06
Glad you solved it, but as you can tell, nobody here was going to know your setup.

Anyways, please mark this thread as SOLVED using the thread tools button, so others seeking a similar answer will find it.  Ah ... I see you just did. Thanks!

---

