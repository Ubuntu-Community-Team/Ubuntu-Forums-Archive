---
title: "Help recomendation of strong security with ubuntu?"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by InfectedJ11 on 2006-10-19
well 2 days ago i installed ubuntu so it is still a fresh copy and today my friend messing around trace my ip and hacked me down in a OS windows now i got rreally piss off because my security wasnt that strong and since i dont know anything about ubuntu can someone tell what do i need to do in order to have a secure and strong sistem help please!!!!!!!!!!!JosueH@linuxmail.org or [email]JosueH@fbi.gov[/email]:(

---

### Post by Dual Cortex on 2006-10-19
Having Linux is already secure enough. MOst 'hackers' are just script-kiddies... most real hackers don't spend/waste their time trying to find exploits for linux.
btw... @**_fbi.gov_**? Are you serious?

](*,) ](*,) :-? :-|

---

### Post by dmizer on 2006-10-19
if he only traced your ip, what's to worry?  your ip needs to be known in order to have internet traffic sent to you (ie receive web pages) ... much like postal mail can't be sent to your house without knowing your street address.

by default, linux does not listen on any ports, so even if he did trace down your ip, there's no real danger unless you have something listening on a public port (ftp server, samba, apache etc.).

this is in contrast to windows, where ports are open and knowing an individuals ip is indeed dangerous.

---

### Post by mssever on 2006-10-19
> **InfectedJ11 said:**
> hacked me down in a OS windows

What do you mean by that? What exactly did your friend get access to? Security is a very broad topic. In general, Ubuntu's default installation is quite secure, but without knowing the specifics of your situation, it's hard to give specific advice.

---

### Post by InfectedJ11 on 2006-10-19
> **mssever said:**
> What do you mean by that? What exactly did your friend get access to? Security is a very broad topic. In general, Ubuntu's default installation is quite secure, but without knowing the specifics of your situation, it's hard to give specific advice.

oh no man i meant that he was in a pc with windows and hacked me down he got access in and told what exactly i had in my pc running at that time i know security in linux is very broad but im just wanting to know like what is the best anti virus, the best firewall and tips so it wont happen again.... [email]JosueH@linuxmail.org[/email] or [email]JosueH@fbi.gov[/email]

---

### Post by InfectedJ11 on 2006-10-19
> **Dual Cortex said:**
> Having Linux is already secure enough. MOst 'hackers' are just script-kiddies... most real hackers don't spend/waste their time trying to find exploits for linux.
btw... @**_fbi.gov_**? Are you serious?

](*,) ](*,) :-? :-|

what are you sorprice of @fbi.gov never hear of it come on easy thing learn how to be a defacer....;)

---

### Post by mssever on 2006-10-20
> **InfectedJ11 said:**
> oh no man i meant that he was in a pc with windows and hacked me down he got access in and told what exactly i had in my pc running at that time i know security in linux is very broad but im just wanting to know like what is the best anti virus, the best firewall and tips so it wont happen again.... [EMAIL="JosueH@linuxmail.org"]JosueH@linuxmail.org[/EMAIL] or [EMAIL="JosueH@fbi.gov"]JosueH@fbi.gov[/EMAIL]

How did he get in? Or, what was exploited? As far as tips to prevent such a break-in goes, we need to know something about the method of attack that was used. Also, what additional exploitable software have you installed (servers, etc.)?

I've heard of ClamAV as an antivirus, but the virus threat in Linux is almost non-existant, so few people use antivirus software in Linux. Smoothwall and Firestarter are two firewalls I know of for Linux; both probably are just front ends for iptables. However, given the inherent security of Ubuntu, it's very unlikely that you would benefit from using a firewall.

You might also be interested in bastille.

Finally, in replying, please remember that your keyboard has punctuation and shift keys for a reason. They make posts *much* easier to understand.

---

### Post by InfectedJ11 on 2006-10-21
well i think he did it byy using xploits because knowing how linux is strong in security he couldnt enter by other method...but thanks..

---

### Post by InfectedJ11 on 2006-10-21
> **mssever said:**
> How did he get in? Or, what was exploited? As far as tips to prevent such a break-in goes, we need to know something about the method of attack that was used. Also, what additional exploitable software have you installed (servers, etc.)?

I've heard of ClamAV as an antivirus, but the virus threat in Linux is almost non-existant, so few people use antivirus software in Linux. Smoothwall and Firestarter are two firewalls I know of for Linux; both probably are just front ends for iptables. However, given the inherent security of Ubuntu, it's very unlikely that you would benefit from using a firewall.

You might also be interested in bastille.

Finally, in replying, please remember that your keyboard has punctuation and shift keys for a reason. They make posts *much* easier to understand.

thanks man one more thing where do i can find the smothwall and firestarter. Also the ClamAv where ? please...:(

---

### Post by Engnome on 2006-10-21
Is there any way he might have figured out your password? Choosing a strong password is probably the best first thing to do to increase security. If your password is based on personal info it's easy to figure out. Then all the hacker has to do is to ssh into your box.

---

### Post by podunk on 2006-10-21
Has your ah, "friend" ever had physical access to your computer? In the same room for a few minutes while you were in another room? You can install all the software in the world but if a hacker can get his hands on your machine it's fairly useless, especially if he knows your password.

To install firestarted and antivirus go to
System
Administration
Synaptic Package Manager
Click it and when it opens click "Search" Enter the program name
When it finds it right click it and chose "Mark for Installation"
Click the green check mark at the top of the screen "Apply"

---

### Post by Zeerak on 2006-10-21
> **InfectedJ11 said:**
> well i think he did it byy using xploits because knowing how linux is strong in security he couldnt enter by other method...but thanks..

well since it's your friend you couldn't ask how he did it? That way others could defend against such attack ask well.

---

### Post by InfectedJ11 on 2006-10-21
thanks man everything help burt he didnt do it by going physically to my pc he did it remotly any ways he tried to hack me back today but my coding in port 8080 and 80 kill he hard drive hehehehehhee my security is tigh man thanks a lot..

---

### Post by blendmaster on 2006-10-21
So, is this like a game or something?

You try to see who can hack who the most/best?

Because I can't imagine being friends with someone who is trying to hack me and still being friends.

If it is a game though, that'd actually be kinda fun (as long as it's not malicious)!

---

### Post by InfectedJ11 on 2006-10-21
> **blendmaster said:**
> So, is this like a game or something?

You try to see who can hack who the most/best?

Because I can't imagine being friends with someone who is trying to hack me and still being friends.

If it is a game though, that'd actually be kinda fun (as long as it's not malicious)!

no man is not a game is a challenge he is not mine friend anymore he is a junk...:mrgreen:

---

### Post by emarkay on 2006-10-21
Get MS-DOS 3.1
Boot
Format C:
Apply needed data.

Then call 911.

Pelligro!:
May cause Cancer in the state of California.
Eat beans, America needs the gas.
Live Long and Prosper.
Klaatu Barada Nikto.
Have a nice day.
Inshallah.
Word.
:)

---

### Post by InfectedJ11 on 2006-10-21
> **emarkay said:**
> Get MS-DOS 3.1
Boot
Format C:
Apply needed data.

Then call 911.

Pelligro!:
May cause Cancer in the state of California.
Eat beans, America needs the gas.
Live Long and Prosper.
Klaatu Barada Nikto.
Have a nice day.
Inshallah.
Word.
:)

hahahahahahahahah i got that.....:twisted:

---

