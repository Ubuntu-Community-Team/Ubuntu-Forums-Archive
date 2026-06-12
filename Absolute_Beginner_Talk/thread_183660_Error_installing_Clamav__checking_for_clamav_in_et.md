---
title: "Error installing Clamav : checking for clamav in /etc/passwd... no"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by Andrew1234 on 2006-05-28
Hi I am trying to install Clamav and am getting an error:-

"checking for clamav in /etc/passwd... no
configure: error: User clamav (and/or group clamav) doesn't exist. Please read the documentation !" 

Can anyone advise me as I have search the forum and cannot find any inform for this.

Thanks

---

### Post by user1397 on 2006-05-28
[quote=Andrew1234]Hi I am trying to install Clamav and am getting an error:-

"checking for clamav in /etc/passwd... no
configure: error: User clamav (and/or group clamav) doesn't exist. Please read the documentation !" 

Can anyone advise me as I have search the forum and cannot find any inform for this.

Thanks[/quote]
do you run a mail server or do you have other windows pc's connnected to your ubuntu box in a network?  if not, there is seriously **_*no*_** point to anti-virus software in ubuntu.  the only reason would be if you had one of the two choices above, which basically means that you want to remove any viruses from mail or possibly infected folders so as not to transfer them to the windows pc's.

---

### Post by Andrew1234 on 2006-05-28
Thanks for your reply,I don't have a windows pc connected a present, but just thought it would be a good idea to have one installed as the pc is only really used for email and internet, I have Firestarter installed OK so from what I can understand this is the most I need for Ubuntu. (Just wondering why do I get the message, and if I would get it for any other install)

Thanks

---

### Post by user1397 on 2006-05-28
[quote=Andrew1234]Thanks for your reply,I don't have a windows pc connected a present, but just thought it would be a good idea to have one installed as the pc is only really used for email and internet, I have Firestarter installed OK so from what I can understand this is the most I need for Ubuntu. (Just wondering why do I get the message, and if I would get it for any other install)

Thanks[/quote]
as you say, a firewall is really all you need (as you may not know, firestarter is just a gui for the ubuntu firewall called iptables) unless you want to safeguard windows pc's, and since you have none, there's no reason at all!  I, for one, don't have an av (anti-virus) and just use firestarter to configure my firewall (though i'm still learning howto!)
as for your exact problem, i don't know how it happened, maybe you installed it from a website instead of using synaptic or the terminal?

---

