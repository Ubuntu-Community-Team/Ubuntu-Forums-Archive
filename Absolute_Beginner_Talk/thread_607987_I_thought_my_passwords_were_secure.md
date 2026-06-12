---
title: "I thought my passwords were secure"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2007-11-09
I just tried this and thought it was interesting enough to share. I dual boot with win xp and I decided that I wanted to see how secure my passwords were. I downloaded Ophcrack and ran it and within a few minutes it had both of my passwords. Pretty neat program. Anyway, is there any easy to use program like that to check password security in Linux?

---

### Post by IamAcoconut on 2007-11-10
*bump*
this is interesting.

PS. If you want security encrypt your hard drive. 7.10 enables you to do this via the alternate CD. I heard of a program enabling Windows to acces LUKS-encrypted volumes.

---

### Post by matthewcraig on 2007-11-10
Passwords are only useful to keep someone off your computer who does not have direct access.  Brute force attacks on a local password hash have always been effective, and they are only getting more effective.  If you'll feel more secure, then chose a longer password, but anyone with direct access to your hard drive ultimately has access to your data.

---

### Post by t0p on 2007-11-10
> **matthewcraig said:**
> Passwords are only useful to keep someone off your computer who does not have direct access.  Brute force attacks on a local password hash have always been effective, and they are only getting more effective.  If you'll feel more secure, then chose a longer password, but anyone with direct access to your hard drive ultimately has access to your data.

All true, of course.  But it would be nice if different users of a machine could feel that their accounts were secure.

---

### Post by matthewcraig on 2007-11-10
> **t0p said:**
> But it would be nice if different users of a machine could feel that their accounts were secure.

How about having them remove their shoes for inspection before allowing them to login?

---

### Post by t0p on 2007-11-10
> **matthewcraig said:**
> How about having them remove their shoes for inspection before allowing them to login?

Nah, I only inspect ears and fingernails. :)

---

### Post by paulbeattie87 on 2007-11-10
Ophcrack is best run from live CD easy way to solve this is to password protect yourr bios and tell it to boot from HDD everytime. Running it in Windows needs to download a lot of large files which takes time.

But as somebody else said anybody who has access to your computer can ultimately get your passwords. On that note you can even use command prompt in XP to get passwords from it! Just know the right commands.

---

### Post by mcduck on 2007-11-10
> **paulbeattie87 said:**
> Ophcrack is best run from live CD easy way to solve this is to password protect yourr bios and tell it to boot from HDD everytime. Running it in Windows needs to download a lot of large files which takes time.

But as somebody else said anybody who has access to your computer can ultimately get your passwords. On that note you can even use command prompt in XP to get passwords from it! Just know the right commands.
BIOS password protection is no use. Just clear the CMOS, and the password is gone. On most computer that takes less than a minute to do. ;)

If somebody can get physical access to a computer, the security is already gone. There really isn't any other way than keeping the machine away from the people you don't trust.

---

### Post by evilregis on 2007-11-10
This is a really good [password strength checker](http://rumkin.com/tools/password/passchk.php).  See how your password that Ophcrack ranks by it.  I've used passwords before that I thought were relatively secure and it ranked them as Weak.

There are lots of ways to make very strong passwords that are not hard to remember.

---

### Post by ghostcrab on 2007-11-10
How long can you make your password in Ubuntu?
Don't the live cd limit your password lent?

---

### Post by Joakim Stokland on 2007-11-10
Damnit! Both my usual passwords were weak and very weak! And those were combinations of letters and numbers, not just a word. AND the one that is "only" weak consists of 10 digits! But then again, I tried to type "WHEN!goTOtheMALL!alwaysBRINGsomeONEwithME?". This one is ranked as overkill. Just for your information! :p

But if the login password is this unsecure locally, will it be any more secure via a network? (Assuming there actually is some program on the computer that responds, and no firewall is enabled)

Joakim

---

### Post by Joakim Stokland on 2007-11-10
Also, I tried one of Ubuntu's auto-generated passwords, and it too was rated very weak.

Joakim

---

### Post by ghostcrab on 2007-11-10
Joakim Stokland try harder

---

### Post by Hairy_Palms on 2007-11-10
my password is my intial followed by the calculator writing of a common word followed by my intial, came out as weak

---

