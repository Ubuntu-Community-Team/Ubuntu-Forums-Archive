---
title: "[SOLVED] Are we safe from police spyware?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-07-18
[FONT=Arial Narrow]Security firms on police spyware, in their own words[/FONT]
[http://news.com.com/2102-7348_3-6196990.html?tag=st.util.print](http://news.com.com/2102-7348_3-6196990.html?tag=st.util.print)
A recent federal court decision raises the question of whether antivirus companies may intentionally overlook spyware that is secretly placed on computers by police.



 Will security firms detect police spyware?   [http://news.com.com/2102-7348_3-6197020.html?tag=st.util.print](http://news.com.com/2102-7348_3-6197020.html?tag=st.util.print)
In a case decided earlier this month by the 9th U.S. Circuit Court of Appeals, federal agents used spyware with a keystroke logger to record the typing of a suspect who used encryption to scramble his communications.


-----
Was that person who was caught by the police using Linux? 
Are Linux users safe from this vulnerablity? What sort of protection do Linux users have? 
How would a Linux user know that there are no trojan horses, keyloggers, spyware on his or her computer?

:(

---

### Post by Hobo Joe on 2007-07-18
Not on MY computer!!!! 


ARRRRGGGG!
Dang police getting in my stuff doesn't make me happy.

---

### Post by Old Pink on 2007-07-18
Get back to prison! ;) 

Yes, you're safe, as far as I know. :D

---

### Post by Wiebelhaus on 2007-07-18
They would have to ask you to do this:

> evilmalware 0.6 (beta)

Copyright 2000, 2001, 2003, 2005
E\/17 |-|4><0|2z Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is
NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT 
DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra 
spams to people accross the world).

Basic Installation
==================

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow 
everything'.

1. Put the attachment into the appropriate directory eg. /usr/src

2. Type `tar xvzf evilmalware.tar.gz' to extract the source files for 
   this virus.

3. `cd' to the directory containing the virus's source code and type
   `./configure' to configure the virus for your system.  If you're
   using `csh' on an old version of System V, you might need to type
   `sh ./configure' instead to prevent `csh' from trying to execute
   `configure' itself.

4. Type `make' to compile the package. You may need to be logged in as 
   root to do this.

5. Optionally, type `make check_payable' to run any self-tests that come 
   with the virus, and send a large donation to an unnumbered Swiss bank 
   account.

6. Type `make install' to install the virus and any spyware, trojans
   pornography, penis enlargement adverts and DDoS attacks that 
   come with it.
  
7. You may now configure your preferred malware behaviour in 
   /etc/evilmalware.conf .

SEE ALSO
   evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1) 

I'd make the gayest "LOL" ever right in their face.

[Link]("http://www.gnu.org/fun/jokes/evilmalware.html")

---

### Post by Hobo Joe on 2007-07-18
> **sx66gns said:**
> They would have to ask you to do this:



I'd make the gayest "LOL" ever right in their face.

[Link]("http://www.gnu.org/fun/jokes/evilmalware.html")

That is fantastic!
Wow, something makes me really wish they would send something like that to me so that I could just say that to them....

Wow that would be hilarious! :P

---

### Post by yabbadabbadont on 2007-07-18
<tinfoil hat mode>Of course, if they really want to get the info regardless of OS, they break in and install a hardware keylogger while you are not home...</tinfoil hat mode>

Actually, that *has* happened in the past, so I guess the tinfoil hat wouldn't help much.  :D

---

### Post by hanzj on 2007-07-18
_@_[sx66gns,]("http://ubuntuforums.org/member.php?u=206596")
So is that the _only_ way to get malware onto a linux computer? Trojan horses don't exist on Linux?

---

### Post by p_quarles on 2007-07-18
My understanding is that Linux is really tough to spy on in this way. I'm sure it can be done, but this kid was probably not using Linux. He actually installed the keylogger himself (not knowing what it was, of course) from an e-mail sent to his MySpace account. Windows could install something like that in the background, without the user ever knowing. In Linux, even if you were dumb enough to log in as root all the time, you would need to go through a few steps to install the software.

EDIT: Those "few steps" being the ones listed in sx66gns's post. :-) As that list points out, you would even get to configure the keylogger after manually installing it.

---

### Post by sad_iq on 2007-07-18
Well the best way to answer is this...There are no viruses for linux(not in the wild at least)...and those that work can't do much to damage the pc.Also the police has no way of installing a keylogger on your pc(you are the only one that can do that..accidentaly maybe :) ) unless they brake into your house...and install a rootkit in there to hide it's presence! Just stick to installing stuff from the official repositories and you'll be ok...the police can't touch them...unless it's a direct order from the president :) (witch will never happen!!!)

---

### Post by hanzj on 2007-07-18
@p_quaries,
Interesting. I wasn't able to read that information (of kid installing keylogger himself from an email sent to his mySpace account). Would you be able to pass on the link to your source article? Thanks.

---

### Post by hanzj on 2007-07-18
@sad_iq
You said "The police can't touch them." What is "them" referring to? The official Ubuntu repositories?

---

### Post by hanzj on 2007-07-18
@Hobo_Joe
Your avatar (of the freaked out pussycat) fits in very well with the topic at hand, and with what you wrote!

---

### Post by Hobo Joe on 2007-07-18
Notice that Mcaffee and Microsoft are the only ones that don't give a direct no to the questions about ignoring certain ones or getting orders from judges.

*sniff* I smell fish.

> =hanzj;3041636]@Hobo_Joe
Your avatar (of the freaked out pussycat) fits in very well with the topic at hand, and with what you wrote!
:D thanks.

I actually think that applies to this one too.....

---

### Post by aysiu on 2007-07-18
That isn't the only way to get malware on a Linux computer. 

Linux programs, like any other programs, have exploits that get discovered and patched. Before they're patched, they usually involve some kind of escalation of privilege or a buffer overflow to execute arbitrary commands.

Then there are some Linux users who choose to do IP forwarding on an SSH server with weak passwords and then get their computers cracked by outsiders.

And, lastly, there's good old social engineering. When we get to the point where some .deb or repositories is cool to have but has fishy (or phishy) software in it, all you'd have to do is double-click and enter your password to give that software full privileges on your system to install spyware.

---

### Post by Brendt2 on 2007-07-18
People in the community would notice if anything like this was even being thought of... and I guarantee that you would see it on slashdot first!  haha!

---

### Post by hanzj on 2007-07-18
[@p_quarles]("http://ubuntuforums.org/member.php?u=290682"),
I found an article talking about the kid who was sent spyware via his MySpace account by the police.  [http://www.wired.com/politics/law/news/2007/07/fbi_spyware](http://www.wired.com/politics/law/news/2007/07/fbi_spyware).

That is a different albeit related story.
Interstingly enough, that spyware is called CIPAV, or  "computer and internet protocol address verifier",  According to the article, CIPAV gathers a wide range of information, including the computer's IP address; MAC address; open ports; a list of running programs; the operating system type, version and serial number; preferred internet browser and version; the computer's registered owner and registered company name; the current logged-in user name and the last-visited URL.  The CIPAV then settles into a silent "pen register" mode, in which it lurks on the target computer and monitors its internet use, logging the IP address of every computer to which the machine connects for up to 60 days. 
 Under a [ruling this month]("http://blog.wired.com/27bstroke6/2007/07/appeals-court-r.html") by the 9th U.S. Circuit Court of Appeals, such surveillance -- which does not capture the content of the communications -- [COLOR=SeaGreen]can be conducted without a wiretap warrant,[/COLOR] because internet users have no "reasonable expectation of privacy" in the data when using the internet.

---

### Post by sad_iq on 2007-07-18
> **hanzj said:**
> @sad_iq
You said "The police can't touch them." What is "them" referring to? The official Ubuntu repositories?
Yes...I do think they can't be touched...too many of them :) Us, Europe... Am I Wrong???

---

### Post by p_quarles on 2007-07-18
hanzj: Oops. I initially assumed you were talking about that story, and didn't click on the link until just now. Sorry. 

That said, I think the vulnerabilities in Linux would mostly involve some level of carelessness on the user's part. Easy passwords, public services, infected packages, etc.

Script vulnerabilities are definitely possible, though, as Aysiu said. As far as I can see, that's pretty much the only way an otherwise secure system/user is going to get seriously hurt. (And this is why I use NoScript in Firefox).

---

### Post by sad_iq on 2007-07-18
Ok...seriously...I think that a guy doing serious illegal stuff(like selling large quantities of drugs) using linux would not be your typical "careless" user...and I don't think that he would be having any public servers running on his machine(I doubt he'll be using ssh to read what and to whom he sold stuff), also social engineering(as aysu suggested) won't have too much effect on such a guy(It's not like someone will call and ask for his password pretending to be the a technician guy...like in the old days)...so to install such a keyloger on his computer would be direct contact with the Pc...or compromise some deb in the repos(but that's like compromising kernel.org and getting away with it). So I think the cops were lucky...the guy was using Windows...witch can be very unsecure by nature...if he were to use linux...they would have been in trouble!!!
 Also a question to aysu...do you think your machine can be compromised without you realizing??? And if so...for how long could they do it???

---

### Post by kittyhawk63 on 2007-07-18
Another protection guaranteed by the Bills of Rights taken away from the people. Police are supposed to issue you a warrant (in your hands) before entering your private premises. Activists judges took care of that. 

Although I am vehemently opposed to socialism and its representatives (because it takes from those who have and gives to those who won't work for it), I must say:
"Orson Wells, you may have been a bit early, but you were not a bit wrong in your prediction of a totalitarian police state." If you are at least my age (in my sixties) you would be upset as I am on how many of our liberties have been taken away in just my lifetime. Because of political correctness running amok, there will be many more liberties lost before many of you reach my age. Just wait and see. I heard my great-grandparents talked about the liberties they had lost during their lifetimes, and now there are even more gone. As long as we have air conditioned and heated halls in Congress, these nuts will continue to steal our liberties. :mad:
kh

Orson Wells charged with believing in Democratic Socialism: [http://www.eeggs.com/items/2038.html](http://www.eeggs.com/items/2038.html)

---

### Post by cleverselfreferentialname on 2007-07-19
My disk is AES-256 encrypted besides the /boot partition. The only way someone with physical access to my machine could install spyware is if he inserted it in the kernel or initial ramdisk itself. Maybe you could do something with an exec parameter on the kernel command line, (modifying the menu.lst) but I don't think that's likely.

I don't run any services, so a buffer overflow would be difficult. I shut off my machine when I'm not here. Law enforcement generally does not have the ability to crack an AES-256 encrypted disk if your passphrase is strong.

Of course, a hardware keylogger would bypass that entirely. I only shut my computer off when I'm /mode +tinfoilhat, and I look for a hwkeylogger when I turn it back on to enter my passphrase.

I'd just like to say that an encrypted filesystem and strong passphrases should be your primary lines of defense if you're concerned about your privacy.

---

### Post by yabbadabbadont on 2007-07-19
> **cleverselfreferentialname said:**
> My disk is AES-256 encrypted besides the /boot partition. The only way someone with physical access to my machine could install spyware is if he inserted it in the kernel or initial ramdisk itself. Maybe you could do something with an exec parameter on the kernel command line, (modifying the menu.lst) but I don't think that's likely.

I don't run any services, so a buffer overflow would be difficult. I shut off my machine when I'm not here. Law enforcement generally does not have the ability to crack an AES-256 encrypted disk if your passphrase is strong.

Of course, a hardware keylogger would bypass that entirely. I only shut my computer off when I'm /mode +tinfoilhat, and I look for a hwkeylogger when I turn it back on to enter my passphrase.

I'd just like to say that an encrypted filesystem and strong passphrases should be your primary lines of defense if you're concerned about your privacy.

That wouldn't do you any good against the suggestion that I made earlier in this thread.  The authorities can, and have in the past, installed **hardware** keyloggers on people's machines while they were away from home.  ;)

Edit: DOH!  I need to learn to read more carefully.  :oops:

---

### Post by p_quarles on 2007-07-19
> **yabbadabbadont said:**
> That wouldn't do you any good against the suggestion that I made earlier in this thread.  The authorities can, and have in the past, installed **hardware** keyloggers on people's machines while they were away from home.  ;)
From the post you quoted:

> Of course, a hardware keylogger would bypass that entirely.

It's definitely true that no software security measures can make a computer safe from physical intrusions. Just like no anti-virus software is going to keep you safe from being picked up by the cops and beaten into confessing something you didn't do. Kinda not the point though.

---

