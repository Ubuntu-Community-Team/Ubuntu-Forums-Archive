---
title: "Ubuntu firewall and anti virus questions"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Roen hayden on 2007-05-20
Ok so for the firewall i'm using firestarter witch just configs ip tables from what i have read.  Now i have also heard that you do not need a anti virus program... so what do you think needed or not cause i do all the security updates so i have security in mind so explain why do i know need anti virus program..  also i  have avg installed but i don't know how to update it keeps say i do not have permission any help?

thanks 
~roen

---

### Post by starcraft.man on 2007-05-20
> **Roen hayden said:**
> Ok so for the firewall i'm using firestarter witch just configs ip tables from what i have read.  Now i have also heard that you do not need a anti virus program... so what do you think needed or not cause i do all the security updates so i have security in mind so explain why do i know need anti virus program..  also i  have avg installed but i don't know how to update it keeps say i do not have permission any help?

thanks 
~roen

There are numerous reasons why you don't need an AV scanner in linux per se. A detailed explaination is [here.]("http://www.psychocats.net/ubuntu/security") 

The gist of it can be summed up as follows. 

1) Running as a limited user (which ubuntu does by default) is a secure way of preventing all modifications to system and administrative applications without password and approval.
2) The linux base is so small that most malware script kiddies don't bother since they want the largest bot nets possible, that means targeting windows exploits and boxes.
3) Linux has a lot of people looking at the code, and I think due to the way its all coded generally has faster turn around time for fixing detected exploits and bugs as well as causing less breakage. It certainly is faster than MS 6 month ANSI fix that screwed up relatek drivers.
4) The default firewall (even without firestarter) is very restricted and prevents most things from entering unwanted.

If you really wish to be that much more secure, my strong recommendation is to be certain you are behind a NAT router.
The best reason for this, is because it will make you invisible on the internet and act as an impenetrable firewall (unless you port forward yourself).

Thats it, have fun :).

---

### Post by ramjet_1953 on 2007-05-20
I second all that starcraft.man said.

The only reason that you may consider using an anti-virus package is if you forward on a lot of emails that have attachments from Microsoft users. This is not to protect you, but the poor sods out there still using Windows.

Another reason may be if you use Wine or virtualisation software to run Windows, or Windows appa.

Regards,
Roger 8-)

---

### Post by starcraft.man on 2007-05-20
> **ramjet_1953 said:**
> I second all that starcraft.man said.

The only reason that you may consider using an anti-virus package is if you forward on a lot of emails that have attachments from Microsoft users. This is not to protect you, but the poor sods out there still using Windows.

Another reason may be if you use Wine or virtualisation software to run Windows, or Windows appa.

Regards,
Roger 8-)

ROFL about the window comment.

Yes, I did forget to mention about virtualization. If you use any virtual environment (or application compatibility layer as WINE likes to be lovingly called...) you may in all likelyhood be prone to a windows virus, as if the API/protocol a Virus looks for is implemented it will assume its in a windows OS.

Oh and one more thing, if you are really paranoid about your XP/Windows install and you have a dual boot, you can scan it while not booted into it.

Those are really the only 3 uses for an AV. If you don't do any of that, don't worry. All them script kiddies love picking on windows users :p

Have a nice day, you too roger.

---

