---
title: "aegis virus scanner"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Architeuthis on 2006-07-28
I discovered the aegis virus scanner yesterday, i installed it without problem.
When i started it asked to update and it asked for my password, after updating it said "please restart aegis". I restarted it and it kept asking for my pass and asking to restart after that.
So i started it with sudo and now a configuring script started when updating, i configured it without problem. Then it checks for updates and runs a script, again it asks to restart. After i restarted it keeps updating and afterwards asking to restart. Can someone help me?

P.S: do i even need an virus scanner or a firewall?

---

### Post by kigina on 2006-07-28
i dont really think a virus scanner is needed
im not gonna say anything about a firewall because i dont know

---

### Post by bigken on 2006-07-28
hi you might be better off using f-prot or even avg if you search the forum for these there are guides on how to install them ;)

---

### Post by eXisor on 2006-07-28
[quote="kigina"]i dont really think a virus scanner is needed[/quote]

Way too trusting, I'm afraid. Unless you isolate the machine completely, of course a virus scanner is needed.

---

### Post by T700 on 2006-07-28
> **eXisor said:**
> Way too trusting, I'm afraid. Unless you isolate the machine completely, of course a virus scanner is needed.

No.  Because of the way Linux is structured, the Windows style viruses are not possible.  There are a small number of worms and exploits, but they are extremely rare and easily defended against.  Unless someone is running a mail server, there is really no reason to run an anti-virus with Linux.  (The only reason to run it with a mail server is to avoid passing infected items to Windows boxes.)

Paul

---

### Post by eXisor on 2006-07-28
Since linux viruses do exist, they certainly can infect your box. Running an antivirus is prudent; for now, and for the future. Don't think virus writers are going to going to keep on ignoring linux forever. The more linux users, the more they have to gain by targetting the platform.

Edit: I'm unsure what you mean by 'structurally'. A c/c++ program changes very little for different platforms. You just compile it with different platform libs.

---

### Post by T700 on 2006-07-28
> **eXisor said:**
> Since linux viruses do exist, they certainly can infect your box. Running an antivirus is prudent; for now, and for the future. Don't think virus writers are going to going to keep on ignoring linux forever. The more linux users, the more they have to gain by targetting the platform.

Edit: I'm unsure what you mean by 'structurally'. A c/c++ program changes very little for different platforms. You just compile it with different platform libs.

Structurally, because without root privilege, there is very little a virus can do, outside of the home directory.  Feel free to run a virus scanner; two it you like.  In my opinion, this is simply new users bringing a Windows mentality to a non-Windows platform.

Paul

---

### Post by eXisor on 2006-07-28
So by your logic it is impossible for a virus to get root privileges? I think not. Difficult, sure. Impossible, no. Do you know for a fact that every program that asks for root priviledges when you install or execute it really needs it? I don't. I either trust the source or I don't, say yes, or no. And I could get it wrong.

My view has nothing to do with windows and related mentality, just being a software engineer for 25 years and knowing 'impossible' often means 'you' may not know how, but someone else does. Anytime a root priviledged program is installed or updated, a root priviledged virus may be installed. As I said, it's all about how much you trust the source, and that's where an antivirus program comes in.

Anyhow, we differ on this which is no biggy. I feel better safe than sorry. You feel safe, and I actually envy you that.

---

### Post by Indras on 2006-07-28
> **eXisor said:**
> Anyhow, we differ on this which is no biggy. I feel better safe than sorry. You feel safe, and I actually envy you that.

My biggest problem with Windows was having to run a virus scanner.  Most modern scanners check every program as it opens, constantly monitors RAM, and even checks outgoing e-mails for the presence of viruses.  This slows a computer down significantly.  With small tasks, it is even more noticeable, since you expect them to complete in under a second and it takes five or six instead.

I actually gave up on virus scanners completely.  Running one on my 1.2Ghz machine made me feel like I was using my first computer again, a 100Mhz Acer Aspire.  So I ran Windows without virus protection for about six years.  I got a couple viruses that I'm aware of, but I've never lost a file that was important to me, or had to do more than fifteen minutes of work to remove them.  I figure that spending fifteen minutes every three years to remove a virus is preferrable to intentionally crippling my machine's every single function to less than half speed.

I guess in a way I view virus scanners like meteor insurance (yes, they sell it).  I mean, yeah, there's a tiny probability that your house will get hit by a meteor and it would be nice to have insurance there to pay for the damages.  Realistically, though, you're just constantly throwing your money in a hole with no chance of it ever coming back.

---

### Post by jimmygoon on 2006-07-28
> **eXisor said:**
> So by your logic it is impossible for a virus to get root privileges? I think not. Difficult, sure. Impossible, no.** Do you know for a fact that every program that asks for root priviledges when you install or execute it really needs it? I don't. I either trust the source or I don't, say yes, or no. And I could get it wrong.**

My view has nothing to do with windows and related mentality, just being a software engineer for 25 years and knowing 'impossible' often means 'you' may not know how, but someone else does. **Anytime a root priviledged program is installed or updated, a root priviledged virus may be installed.** As I said, it's all about how much you trust the source, and that's where an antivirus program comes in.

Anyhow, we differ on this which is no biggy. I feel better safe than sorry. You feel safe, and I actually envy you that.

A virus scanner isn't going to prevent that...

---

### Post by eXisor on 2006-07-28
If it is a virus infected install it will. If it is a maliscious program it won't.

---

### Post by steve.horsley on 2006-07-28
> **eXisor said:**
> Since linux viruses do exist, they certainly can infect your box. Running an antivirus is prudent; for now, and for the future. 

As and when a real Linux virus appears in the wild then it will be prudent to take precautions against it , either by installing a virus scanner or much better, installing the patches to close the vulnerability. But at the moment, there are no Linux viruses in the wild, and therefore nothing to look out for. What's a virus scanner supposed to do? All it can do is look for all the thousands of known Windows viruses.

---

### Post by newagelink on 2006-07-28
> **T700 said:**
> Structurally, because without root privilege, there is very little a virus can do, outside of the home directory.Couldn't a virus just grab your password the next time you sudo, and then have its way with your / directories?

---

### Post by steve.horsley on 2006-07-29
> **newagelink said:**
> Couldn't a virus just grab your password the next time you sudo, and then have its way with your / directories?

Yes. It would be trivial to hide itself and amend .bashrc to launch itself whenever you log in. And I _think_ it could probably monitor your keystrokes waiting for the sudo password - or a credit card number. I'm sure viruses and worms will appear for Linux eventually.

---

