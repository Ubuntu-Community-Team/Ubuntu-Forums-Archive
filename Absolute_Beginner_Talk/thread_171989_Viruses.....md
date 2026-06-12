---
title: "Viruses...."
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-05-07
Hi,
I wonder if there is a Virus risk and what Anti Virus package is recommended to install, to protect my computer?
cheers 
juergen

---

### Post by NeghVar on 2006-05-07
AVG is available from there website, search avg free on google.

ClamAV is a CLI option in the repositories, Aegis is a gui that i have never had any luk with also in the repositories, just search synaptic for each name, im not sure but u may have to add a repository.

Viruses dont really exist for linux, the best reason to have a scanner is to protect yr underprivilaged friends and family that use windows or if u also run windows

---

### Post by nalmeth on 2006-05-07
Don't worry about infecting your linux system with viruses. It won't happen. I won't go into details here, but search the forum, or google with linux and viruses, and you will soon see it is not an issue you will have to worry about.
If you want to scan your emails to prevent *passing on *viruses to contacts, then there are a few linux clients that can do this.
Welcome to a sanitary computing environment!

---

### Post by az on 2006-05-07
[QUOTE=Cariboo1938]Hi,
I wonder if there is a Virus risk and what Anti Virus package is recommended to install, to protect my computer?
cheers 
juergen[/QUOTE]

There is far greater risk to installing a proprietary anti-virus app than doing nothing, insofar is Ubuntu is concerned.  There is no real risk.  Windows is prone to viruses because of the way it is built, but linux/Unix is not built that way.  

If there ever will be such vulnerabilities, an appropriate application will become a dependency for the ubuntu-desktop meta-package and everyone will get one installed via security updates, I guess.

---

### Post by 5-HT on 2006-05-07
[quote=azz]There is far greater risk to installing a proprietary anti-virus app than doing nothing, insofar is Ubuntu is concerned...[/quote]

Hi, are you referring to a risk in actually getting a proprietary anti-virus application to install and function properly in Ubuntu without conflicting with anything else, or rather the general risk of installing a proprietary and closed-source application?

---

### Post by az on 2006-05-08
[QUOTE=5-HT]Hi, are you referring to a risk in actually getting a proprietary anti-virus application to install and function properly in Ubuntu without conflicting with anything else, or rather the general risk of installing a proprietary and closed-source application?[/QUOTE]
The latter, since I hadn't though of the former - maybe both?

---

### Post by gr0kzer0 on 2006-05-08
As everyone has been pointing out, there's virtually no virus risk with Linux. This is due both to the structure of Linux, and the fact Linux is at present a lot less common than Windows.

However, I think it's worth remembering that *nix systems are _not_ immune to malware, no matter what some users believe.

Ever heard of the Morris Worm? The "first worm/virus on the internet"? Well, that was a Unix worm - it made use of a vulnerability in an old version of sendmail. And there have been others too. Remember, before Windows became so widespread, the internet was pretty much made up of Unix systems. Linux is a *nix. And malware has been round a lot longer than Windows.

Yes, the *nix structure _is_ inherently more secure than Windows. But it is still possible to create malware that can get root on Linux. And as Linux gets more popular, more virus writers are going to turn their attention to us.

I'm not trying to be a doom-sayer, nor am I trying to get people paranoid. We are all pretty safe from viruses at the moment. But it's worthwhile bearing in mind that could change.

---

### Post by whatrucrazy on 2006-05-08
[QUOTE=NeghVar]AVG is available from there website, search avg free on google.
[/QUOTE]

i noticed on the avg webiste ([http://free.grisoft.com/doc/20/lng/us/tpl/v5](http://free.grisoft.com/doc/20/lng/us/tpl/v5)) that they now have a linux version - so is it good for ubuntu (all the debates over the necessity or not of anti-virus software aside)?
if so which package: the rh, suse, or mdk?

then again - who knows anyone running *nix where a virus or malware have *actually* been a problem?

---

### Post by nocturn on 2006-05-08
[QUOTE=gr0kzer0]As everyone has been pointing out, there's virtually no virus risk with Linux. This is due both to the structure of Linux, and the fact Linux is at present a lot less common than Windows.

However, I think it's worth remembering that *nix systems are _not_ immune to malware, no matter what some users believe.
[/QUOTE]

I agree.  But I would also like to point out that AV is a flawed response to the malware problem.   It relies completely on your AV engine, which may not detect certain malware by accident (too new, a variant, ...) or deliberately (the Sony rootkit).

Don't get me wrong, AV and things like rkhunter are fine tools when you have a reason to suspect infection.  But AV is not a prevention system it's hyped to be.

To protect yourself against viruses, get a good firewall, if you want to augment that, get outboud filtering too, keep your system patched and do not install or run untrusted software.

---

### Post by nocturn on 2006-05-08
[QUOTE=whatrucrazy]i noticed on the avg webiste ([http://free.grisoft.com/doc/20/lng/us/tpl/v5](http://free.grisoft.com/doc/20/lng/us/tpl/v5)) that they now have a linux version - so is it good for ubuntu (all the debates over the necessity or not of anti-virus software aside)?
if so which package: the rh, suse, or mdk?

then again - who knows anyone running *nix where a virus or malware have *actually* been a problem?[/QUOTE]

Indeed, and as the AV software is closed source, how do you know what it actually does?

I was very shocked to learn that most AV engines deliberatly ignored the Sony rootkit on Windows.

---

### Post by Sef on 2006-05-08
> As everyone has been pointing out, there's virtually no virus risk with Linux. This is due both to the structure of Linux, and the fact Linux is at present a lot less common than Windows.


If a virus got into your system, you might lose some documents, but that would really be it.  To affect the system you would have to allow it to.

---

### Post by purdy hate machine on 2006-05-08
[QUOTE=nocturn]I was very shocked to learn that most AV engines deliberatly ignored the Sony rootkit on Windows.[/QUOTE]

Would the average AV application on Windows usually detect Rootkits then?

---

### Post by Omnios on 2006-05-08
Im torn between having a anti virus and going without. On one hand I would like to run a anti virus but on the other I found clam took up a lot of resources. Maybe Avg is better which I have but then I have to do scans. All my email is my_isp_Yahoo.webmail so no problems there. Guess its a personal choice rather than a specific need.

---

### Post by phil66 on 2006-05-08
New virus threatens Linux and Windows PCs

Virus writers have released Bi, a malware targeting both Linux and Windows, according to Kaspersky Labs. The malware targets the ELF (Executable and Linking Format) and PE (Portable Executable) file formats used in executables, including Windows' .exe and .dll files. The virus is only a proof-of-concept, however, such proofs are usually followed by a malicious version. The SANS Institute warns that Linux and Mac OS X users must drop their sense of invulnerability against viruses and start protecting themselves with antivirus products.

[http://www.techworld.com/security/ne...fm?NewsID=5752](http://www.techworld.com/security/ne...fm?NewsID=5752)

All threads concerning use of anti-virus programs in Linux have a tendency to discourage users from installing protection.

Does not this script show that it is inevitable that Linux will be attacked and would it not be wise to start using protection now?

---

### Post by Perfect Storm on 2006-05-08
Well that would required that you sudo sh <virus>.sh to activate it if I'm not wrong.
By the way the link doesn't work.

---

### Post by steve.horsley on 2006-05-08
[QUOTE=phil66]
Does not this script show that it is inevitable that Linux will be attacked and would it not be wise to start using protection now?[/QUOTE]
There is no point whatsoever in installing an antivirus program for a virus that doesn't exist yet. AV programs are not predictive, they can only recognise known signatures. Once a real Linux virus shows up in the wild (and it will, I guess), then the AV packages will add it to their scanner libraries and we can all install AV software. But at the moment there is nothing to look for.

If you often exchange files with Windows users, you may chose to install AV to prevent the transfer of known viruses from MS->Linux->MS though.

---

### Post by az on 2006-05-08
[QUOTE=Sef]If a virus got into your system, you might lose some documents, but that would really be it.  To affect the system you would have to allow it to.[/QUOTE]

No.  There are several ways that malware in general can escalate priviledges and become root.  Google for "smash the stack for fun and profit".

If you stay up to date with your security updates, you should stay ahead of such vulnerabilities.  Viruses are different, in that they exploit vulnerabilities that cannot be closed in windows - which is why you have to scan for them, instead of just closing the holes.

The reason there are linux versions of anti-virus software is mainly for mail servers who need to scan outgoing mail for viruses.  It's is pretty dumb to run a mail server on a desktop system.

---

### Post by TeeAhr1 on 2006-05-08
btw, the plural of virus is *virii* (VI-rye).

---

### Post by aysiu on 2006-05-08
[QUOTE=TeeAhr1]btw, the plural of virus is *virii* (VI-rye).[/QUOTE] [Actually, the plural of *virus* is *viruses*.](http://dictionary.reference.com/search?q=virus)

---

### Post by az on 2006-05-08
[QUOTE=TeeAhr1]btw, the plural of virus is *virii* (VI-rye).[/QUOTE]
Latin fourth declension 

Singular
Nominative &#8211;us 
Genitive &#8211;&#363;s 
Dative &#8211;u&#299; 
Accusative &#8211;um 
Vocative &#8211;us 
Ablative &#8211;&#363; 
Locative &#8211;&#363; 

Plural 
Nominative &#8211;&#363;s 
Genitive &#8211;uum 
Dative &#8211;ibus 
Accusative &#8211;&#363;s
Vocative &#8211;&#363;s  
Ablative &#8211;ibus 
Locative &#8211;ibus

---

### Post by Omnios on 2006-05-08
I think one of the niceties of Ubuntu is not having to log on and spend hours updating and running anit virus, anti spyware and maleware programms!

---

### Post by user1397 on 2006-05-08
[quote=Omnios]I think one of the niceties of Ubuntu is not having to log on and spend hours updating and running anit virus, anti spyware and maleware programms![/quote]
Word. 8)

---

