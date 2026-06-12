---
title: "Internet/Network related question"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Holy Knight on 2007-08-19
OK...this is really not a serious problem but its kind of annoying.

You see every time I try to open a web page(through FireFox) it ask me for my unique username and password (authentication required).Similarly when I try to access my network in a domain.

In XP after setting up the domain name and then joining the domain using Network Identification Wizard(with a unique Computer name),it automatically creates a Windows account(assigned by the network administrator) from which I can easily log on with full access.

So what should I do to make similar configuration in Ubuntu so that I don't have to mention my username and password everytimeI try to browse the Internet and get full access to my network's resources?

---

### Post by jamvegan on 2007-08-19
This is not an area I have any experience in, but to try to help point you in the right direction...

Do you know what kind of authentication is used on your network?  For instance, if it's LDAP, then this Ubuntu community documentation might help you: [LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication").

If your network uses another form of authentication, try searching the documentation and/or forums specifically for that authentication scheme, or ask about it by name.  The more information you can provide, the better.

Good luck! :-)

---

### Post by Holy Knight on 2007-08-19
> **jamvegan said:**
> This is not an area I have any experience in, but to try to help point you in the right direction...

Do you know what kind of authentication is used on your network?  For instance, if it's LDAP, then this Ubuntu community documentation might help you: [LDAPClientAuthentication]("https://help.ubuntu.com/community/LDAPClientAuthentication").

If your network uses another form of authentication, try searching the documentation and/or forums specifically for that authentication scheme, or ask about it by name.  The more information you can provide, the better.

Good luck! :-)

OK...I will ask my network administrator about the authentication type.Please be patient,I may not reply for a while because of Internet problem :(.

---

### Post by Holy Knight on 2007-08-20
I am not sure how to say this..since I don't have much knowledge about networking.Well.. for a start I have a wired LAN connection and my network uses a domain type authentication(with static IP)..or in short a DynamicDNS.

I hope I am not confusing you.

---

### Post by Holy Knight on 2007-08-22
hello?anyone?:(

---

### Post by jamvegan on 2007-08-22
Holy Knight,

Sorry that no one has been able to help you yet.  I have no experience with authenticating against a Windows network (which seems to be your case).  It seems like what you've described may be Active Directory authentication?  If so, here are a couple of links that I found that might help you:

[HOWTO: Configure Ubuntu for Active Directory Authentication]("http://developer.novell.com/wiki/index.php/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication") (on Novell's website)

[HOWTO: Active Directory Authentication]("http://ubuntuforums.org/showthread.php?t=91510") (here in the Ubuntu forums)

You might also watch for any replies on this thread:
[Active Directory Authentication on log-in]("http://ubuntuforums.org/showthread.php?t=532197")

I hope one of these links helps, or someone else finds this thread who really understands your problem!

jamvegan

---

