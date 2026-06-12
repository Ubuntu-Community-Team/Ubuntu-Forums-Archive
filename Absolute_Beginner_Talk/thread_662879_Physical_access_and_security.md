---
title: "Physical access and security"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by MalfunctioningMartian on 2008-01-09
Everywhere I read: if someone has physical access to your machine, all security is lost. Is it really as bad as all that?

What about whole disk encryption with strong regularly changed password? As I have it it will take a *very* long time to get in.

---

### Post by LowSky on 2008-01-09
> Everywhere I read: if someone has physical access to your machine, all security is lost. Is it really as bad as all that

its the same as someone having access to your home. why would you give away your passwords or keys if you dont trust them. In the end it all comes down to how parnoid you are about your information.

---

### Post by asmoore82 on 2008-01-09
Personally, I'm from the camp that is strongly opposed to full disk and or boot block encryption
and feel that it is a complete waste of time.

It is old time UNIX SysAdmin wisdom that as soon as someone has physical access to the machine,
all security is lost. Now with modern uber-encryption scheming, you can slow down the intruder
quite a bit. However, I always like to point out that you must take a step back and a deep breath
and realize the loonacy of the situation: you are attempting to use **logical** means(software)
to impose **physical** securtiy. If your situation is truly so dire, hire armed guards.
(In the end, this would also serve your local economy far better)

Finally, and on a much more serious note, you must realize that if/when physical security is
compromized; all of your efforts can only slow down the intrusion process; not stop it.
If whomever has physical access, they can steal the computing device alltogether and
after that, if they really want to access your data that badly, it is only a matter of time.

---

### Post by MalfunctioningMartian on 2008-01-09
> Finally, and on a much more serious note, you must realize that if/when physical security is
compromized; all of your efforts can only slow down the intrusion process; not stop it.

Is there much difference between stopping someone and slowing him a hundred years? I was under the impression that it would take more than a lifetime to crack a tough password for a modern algorithim. Is this incorrect?

> 
If your situation is truly so dire, hire armed guards.

I am more a curious newbie than someone who actually needs encyption. But I figured asking was OK because the topic says '...to find out more...'

---

### Post by eolson on 2008-01-09
If I want you info,  I'll just take the whole machine with me.  That way I've got the info and the machine.  Actually,  there is a benefit to having it secure enough so the perpetrator has to take the whole machine or take the drive.  You know he has it.  If he can access the data without leaving a trail you don't know.

---

### Post by Niniel on 2008-01-09
No, it's not.

When the whole disk is encrypted, nothing is lost. Well, your data may be toast, but the attacker won't get in. I don't care what all the old Unix admin books in the world say, they were all written before the advent of strong encryption and are therefore, in my opinion, trash as far as this application is concerned.

Good encryption is unbreakable as of right now, although that may change in the future. 

Just set things up correctly, i.e. have a good, long password, and/or keyfiles (TrueCrypt uses those). 

Btw, with disk encryption - be that full disk or virtual disk (containers) encryption, you CANNOT change the password without losing all your data. So do it right the first time (or move your data to another encrypted drive, then delete your first drive, set it up again, and copy the data back). 

Having said that, physical security may matter in a different way. Since the encryption is totally unbreakable/unbreakable in a reasonable amount of time, physical access to your machine may be used to obtain your password. That is actually a much more likely vector of attack than brute force. In case of the government, they may attempt to "convince" you to give them the key. 

To summarize, with good encryption, safeguarding your key/s is key; as long as that's not compromised, your data is quite safe (some encryption may be more vulnerable to attack than other though, eg. a cryptologist recently discovered a potential problem with public key encryption that might enable an attacker to break in quite easily; as far as I know, that's more of a theoretical problem at the moment).

---

### Post by asmoore82 on 2008-01-09
> **MalfunctioningMartian said:**
> Is there much difference between stopping someone and slowing him a hundred years? I was under the impression that it would take more than a lifetime to crack a tough password for a modern algorithim. Is this incorrect?

machines are getting faster everyday

> **MalfunctioningMartian said:**
> I am more a curious newbie than someone who actually needs encyption. But I figured asking was OK because the topic says '...to find out more...'
I wasn't refering to you personally.

Another issue I thought of is those poor unfortunate souls on non-linux systems:
What if they have full disk encryption but pick up some trojan or backdoor that sends
copies of their data to intruders while they are using the computer?
In that case, what can we say to that individual?
"Congratulations on your unbreakable full disk encryption!
Fortunately for the intruder, you were nice enough to decyrpt the data **for** them."

---

### Post by TheWizzard on 2008-01-09
> **MalfunctioningMartian said:**
> Everywhere I read: if someone has physical access to your machine, all security is lost. Is it really as bad as all that?

without encryption: yes. 


> **MalfunctioningMartian said:**
> What about whole disk encryption with strong regularly changed password? As I have it it will take a *very* long time to get in.

there are disadvantages on encrypting your entire drive. just encrypt the information you really consider confidential.

---

### Post by mister_pink on 2008-01-09
> **asmoore82 said:**
> machines are getting faster everyday

This is a case of if I start a brute force attack now it'll take x years (where x is too big to worry about anyway, ie thousands of years). If I start in 5 years say, it'll take x/2 years because computers will be quicker. If I start in 10 years, x/4. So I just won't bother starting until its got to the point where it can be decrypted in hours rather than centuries ;) Modern encryption, properly applied, is going to remain unbreakable for a long time.

If you were wondering about file read/write permissions protecting your data, try sticking in the live CD.

I think the point most people are missing here is that unless you store your bank login details in plain text, if someone gets physical access to your machine you'll be more pissed that they broke into your house, stole your computer, TV etc than that they also got a copy of your complete star trek TNG collection or whatever ;)

---

### Post by p_quarles on 2008-01-09
Just wanted to add: encrypting data doesn't prevent anyone from just deleting the containers or formatting the drive.

---

### Post by MalfunctioningMartian on 2008-01-10
Thanks a lot for the help.

---

### Post by nocturn on 2008-01-10
> **asmoore82 said:**
> 
Finally, and on a much more serious note, you must realize that if/when physical security is
compromized; all of your efforts can only slow down the intrusion process; not stop it.
If whomever has physical access, they can steal the computing device alltogether and
after that, if they really want to access your data that badly, it is only a matter of time.

I'm sorry, but I disagree completely.  Sometimes data needs to be secure even though it can be stolen easily.  To date I have never heard that stolen data that is encrypted securely (PGP for example) has been compromised.

BTW, you cannot physically secure something like a laptop or PDA, systems like DM-crypt and truecrypt are the only means to protect your data.  If you have any information that it is feasible to break them, I'd like to see it...

---

### Post by nocturn on 2008-01-10
> **asmoore82 said:**
> machines are getting faster everyday


Yes, but yet, data I encrypted with my PGP key in 1999 still cannot be cracked in a reasonable time today, even with access to a beowulf cluster.  
So, it kept my data safe for 9 years and counting, not to mention that access to the needed resources (like a cluster) is very uncommon.

---

### Post by nocturn on 2008-01-10
> **p_quarles said:**
> Just wanted to add: encrypting data doesn't prevent anyone from just deleting the containers or formatting the drive.

True, but if they stole a laptop/harddrive/USB key with the data on it, you already lost it.
That is what backups are designed to protect and they handle encrypted containers very well.

---

### Post by hyper_ch on 2008-01-10
Well, there are some encryption methods that are considered weak now as collissions could be made a lot more often than orginally expected. Also the adavance of rainbowtables is progressing... so if you want to full encrypt you drive you should also have a very strong passsword to it...

Eventually it's all crackable with bruteforce but the question remains in what timeframe access is needed to that specific data? I tend to think that normally timeframes don't range for several years and with todays encryption mechanism you can slow them down this much.

---

### Post by nocturn on 2008-01-10
> **hyper_ch said:**
> Well, there are some encryption methods that are considered weak now as collissions could be made a lot more often than orginally expected. 


Collisions are not about encryption, but about hash functions.  They have been found for md5 and SHA-1, but this does not yet mean that I can produce a file or mail with different sensible content with an identical hash to a file you have, which would mean a real world break of the fuction.

> 
Eventually it's all crackable with bruteforce but the question remains in what timeframe access is needed to that specific data? I tend to think that normally timeframes don't range for several years and with todays encryption mechanism you can slow them down this much.

For a decent sized PGP key, the timeframe for feasable brute force attacks ranges into the decades.  AFAIK, even a medium-sized cluster cannot break a PGP encrypted message in years.

---

### Post by sailor2001 on 2008-01-10
> **Niniel said:**
> No, it's not.

When the whole disk is encrypted, nothing is lost. Well, your data may be toast, but the attacker won't get in. I don't care what all the old Unix admin books in the world say, they were all written before the advent of strong encryption and are therefore, in my opinion, trash as far as this application is concerned.

Good encryption is unbreakable as of right now, although that may change in the future. 

Just set things up correctly, i.e. have a good, long password, and/or keyfiles (TrueCrypt uses those). 

Btw, with disk encryption - be that full disk or virtual disk (containers) encryption, you CANNOT change the password without losing all your data. So do it right the first time (or move your data to another encrypted drive, then delete your first drive, set it up again, and copy the data back). 

Having said that, physical security may matter in a different way. Since the encryption is totally unbreakable/unbreakable in a reasonable amount of time, physical access to your machine may be used to obtain your password. That is actually a much more likely vector of attack than brute force. In case of the government, they may attempt to "convince" you to give them the key. 

To summarize, with good encryption, safeguarding your key/s is key; as long as that's not compromised, your data is quite safe (some encryption may be more vulnerable to attack than other though, eg. a cryptologist recently discovered a potential problem with public key encryption that might enable an attacker to break in quite easily; as far as I know, that's more of a theoretical problem at the moment).

tsk tsk  Is someone trying to say the pentagon never gets hacked?

---

### Post by Niniel on 2008-01-10
> **sailor2001 said:**
> tsk tsk  Is someone trying to say the pentagon never gets hacked?

Not sure what hacking Pentagon computers has to do with the question. 
If the attacker manages to break into a running system with encrypted files/partitions/disks open, then I guess he'll be able to access those. But if he were to physically steal a drive, when it's encrypted he won't be able to read it. 
Various US government agencies have lost laptops fairly recently with thousands of people's personal data on it, and in most cases it sounded like their only "defense" against data theft had been obscure applications/data formats. If those incidents don't drive home the need for encryption, then I don't know what will.

---

### Post by asmoore82 on 2008-01-10
Wasn't there recently a big botnet bust where the kid had control of over 1 million PCs?

That's the type of individual who would be attempting to crack your full drive encryption.
And the most recent theory I've heard on bruteforce cracking said it would take 40 years.
Well, 40 years, with 365 days in each and 24 hours in each day, is equal to 350400 hours.
This means that if it would take 1 computer 40 years(350400 hours), a botnet of only
250,000 could get it done in about 1.4 hours.

Also bear in mind that corporate BigWigs are using the hollow promise of "unbreakable" full-drive encryption
as a Trojan Horse to get Trusted(read: Treacherous) Computing initiatives off the ground and into
consumers' hands; which in the long run will serve to lock out Linux and other Open Source developers.

---

### Post by Niniel on 2008-01-10
> **asmoore82 said:**
> Wasn't there recently a big botnet bust where the kid had control of over 1 million PCs?

That's the type of individual who would be attempting to crack your full drive encryption.
And the most recent theory I've heard on bruteforce cracking said it would take 40 years.
Well, 40 years, with 365 days in each and 24 hours in each day, is equal to 350400 hours.
This means that if it would take 1 computer 40 years(350400 hours), a botnet of only
250,000 could get it done in about 1.4 hours.

Also bear in mind that corporate BigWigs are using the hollow promise of "unbreakable" full-drive encryption
as a Trojan Horse to get Trusted(read: Treacherous) Computing initiatives off the ground and into
consumers' hands; which in the long run will serve to lock out Linux and other Open Source developers.

Lol, this has nothing to do with "big business", after all TrueCrypt is Open Source, and Ubuntu also comes with full disk encryption (alternate CD) - I doubt any of those parties are offering that for monetary gain or in order to establish TC.
And as for that "taking out" Open Source, I don't think so. Open Source is big enough that it can survive on its own. 

Also, I'm pretty sure there's a flaw in your estimate of how quickly encryption can be cracked. (Where did you learn that it'll take a single computer exactly 40 years to crack any encryption?) Massively parallel computing has been around for years, and if that worked, encryption would be pointless.

---

### Post by thelatinist on 2008-01-10
> **mister_pink said:**
> I think the point most people are missing here is that unless you store your bank login details in plain text, if someone gets physical access to your machine you'll be more pissed that they broke into your house, stole your computer, TV etc than that they also got a copy of your complete star trek TNG collection or whatever ;)

Ha!  So true.  The greatest protection we have for our data is the fact that nobody has any interest in any of it.  I can guarantee that there is nothing on my computer that's worth burglarizing my apartment for.  If you're guarding important financial records for a company, then you better have security procedures, protocols for who gets access to data, and physical security for your system.  Personally, I'm not worried about someone getting hold of my browser cache or my term papers.

---

### Post by nocturn on 2008-01-11
> **asmoore82 said:**
> Wasn't there recently a big botnet bust where the kid had control of over 1 million PCs?

That's the type of individual who would be attempting to crack your full drive encryption.
And the most recent theory I've heard on bruteforce cracking said it would take 40 years.
Well, 40 years, with 365 days in each and 24 hours in each day, is equal to 350400 hours.
This means that if it would take 1 computer 40 years(350400 hours), a botnet of only
250,000 could get it done in about 1.4 hours.


Your equation is flawed in so many ways.
Though you could use a grid to crack and attack passwords and hashes, encryption would require the nodes to have access to the encrypted data, which would mean distributing the content of a HD to all participating nodes, which is not feasable.

And then still, only one drive would be broken....

Not to mention that I do not believe a single node can crack schemes like truecrypt in 40 years, let alone something like PGP.

---

