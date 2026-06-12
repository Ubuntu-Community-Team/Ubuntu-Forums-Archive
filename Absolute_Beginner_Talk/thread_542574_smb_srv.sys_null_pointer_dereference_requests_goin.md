---
title: "smb srv.sys null pointer dereference requests going out from my pc :-("
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by fordnotprefect on 2007-09-04
Help!!

I've been running ubuntu on my work machine for past 2 years without getting into any sort of trouble.
But recently security caught up with me saying there were a lot of malformed smb requests originating from my machine causing srv.sys null pointer dereferences on a particular server. I dont remember having anything to do with that particular server and am completely clueless. Where do I start checking? Does anyone know of any such vulnerability?

Please dont let them force me back to windoze!! 

Thanks

---

### Post by nowshining on 2007-09-04
first thing is to run updates and make sure everything is updated...

---

### Post by fordnotprefect on 2007-09-04
I must admit I had run it for around 3 months without updates (stupid user error, I know) and updating was the first thing I did after the incident.

Is there any specific vulnerability that could have caused this? What should I do if I am already infected?

Thanks a lot.

---

### Post by nowshining on 2007-09-04
where did you find out that these certain packets were leaving your compuer?

linux normal log
programs log

?? what ??

---

### Post by fordnotprefect on 2007-09-04
I do not have any log or trace of it on my machine. The admins of the server detected the intrusion as a possible dos attack, got the ip, found it to be mine and sent me a warning mail.

Which log should I check?

---

### Post by nowshining on 2007-09-04
hmm well any ip can be spoofed to look like it was from your computer if not examined in detail as just picking an ip and going to whois it won't help again like I siad it could be spoofed. :(

hmmm has anyone else been on your computer lately besides you???

---

### Post by fordnotprefect on 2007-09-04
Yeah, true.. Thats not a proper proof, but enough for the security group :-(
Another person using ubuntu within office network also had the same kind of packets sent from his PC. That was an up-to-date system.

No one else uses my computer.

---

### Post by scxtt on 2007-09-04
do you use samba in any way (shares from your PC, connecting to shares on a windows PC {"particular server"})?

---

### Post by fordnotprefect on 2007-09-04
Yes. Thats how I share and access other Windows PC shares. But I dont think I tried to access anything from the server which was attacked.

Thanks a lot guys for your help :-)

---

### Post by scxtt on 2007-09-04
looks to be more of a problem w/ windows:

[http://www.security-mob.com/my_smob/alert_info.asp?alert=41318](http://www.security-mob.com/my_smob/alert_info.asp?alert=41318)
[http://xforce.iss.net/xforce/xfdb/29204](http://xforce.iss.net/xforce/xfdb/29204)

---

### Post by fordnotprefect on 2007-09-04
Yes. And the admins are after me saying I sent around 500 of those specially crafted messages. Similar packets went from another ubuntu running computer too.

---

### Post by scxtt on 2007-09-04
it's not your fault, or your problem - you have no malicious intentions (i presume) and (if) your box isn't under the control of someone who does, i fail to see why they want to punish you for a "windows problem" ...

try using a live CD for the entire day - see if they get any requests ...

---

### Post by fordnotprefect on 2007-09-04
There were a lot of packets sent on 20th and 27th last month. Nothing since that.
How do I find out if my computer has been compromised? Or does samba does some sort of intelligent scanning (which coincidently happen to send the malformed messages)?

To use ubuntu in a Windows network, I might be needing a thousand approvals. I'm trying to get this thing sidelined without attracting much of an attention. My only hope.

---

### Post by scxtt on 2007-09-04
can they give you a timestamped log of what they're seeing?  maybe you can track what you're doing (samba wise) and see what matches up ...

not sure how you could find out if it's been compromised, try running "last" from a terminal and see if you see any logins for times where you weren't there ... i think a liveCD would give you a "fresh start" w/o affecting your current install ...

are you just mounting windows SMB share once and leaving them connected all shift?  or are you constantly browsing samba shares on the network?

my overall feeling is that there are just subtle differences in the way SMB requests are processed by windows/linux - seems really lame for them to blacklist you using ubuntu for that ... i could see them doing it if the server goes down and there's a timestamp in a log they can track to you, as it stands it seems to me they're just FUD'ing the whole situation ...

---

### Post by fordnotprefect on 2007-09-04
Couple of the requests were when I was away from my computer (locked).
I checked 'last' and there were no logins apart from mine for those days.

I connect thru smb only when I need to access something and disconnect as soon as I am done. Neither do I keep any shares mounted (apart for one other server which I mounted using webdav), or browse thru the samba shares.

Maybe its because the way the requests are handled by the server. Let me see running from live cd for a few days :-)

Thanks!

---

### Post by scxtt on 2007-09-05
let me know what happens - where i work, were pretty tied to MS (Active Directory and all that) - i've been considering booting something like SLAX off a USB drive so i can use Linux to do more or less every day to day task ... just have to figure out a way to get some goofy (windows only provided) Java programs running (monitoring tools) - maybe off the management server? ...

---

### Post by fordnotprefect on 2007-09-11
I ran smbstatus and saw that there are two smbd running and one of them was actually connected to the server in question. Also, in the /var/log/samba/ directory I see around 400 log files (one log file for almost every machine on the network!). 

This is an entry from the log file corresponding to the attacked server
```

[2007/08/10 11:10:33, 0] auth/auth_util.c:create_builtin_administrators(785)
  create_builtin_administrators: Failed to create Administrators
[2007/08/10 11:10:33, 0] auth/auth_util.c:create_builtin_users(751)
  create_builtin_users: Failed to create Users

```

Does samba does any sort of scanning of the network?

:-(

---

### Post by fordnotprefect on 2007-09-11
In my System-> Administration -> Network -> General tab, the Automatic Service Discovery is checked. What does this do?

Could this be sending the samba requests?

---

