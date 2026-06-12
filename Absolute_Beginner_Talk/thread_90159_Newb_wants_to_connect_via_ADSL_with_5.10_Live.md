---
title: "Newb wants to connect via ADSL with 5.10 Live"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by drjaycee on 2005-11-14
Hi, Am an abs newbie and would like to know if it is possible to configure ADSL modem to connect to the net using Live CD 5.10?
Did sudo pppoeconf from terminal and followed all prompts and after finishing typed plog which said that could not connect and " the username or password is incorrect" . I am on XP and when connecting from there the same username and passwords work.Where have I gone wrong?
I'll be thankful for any help.

---

### Post by Kapre on 2005-11-14
[QUOTE=drjaycee]Hi, Am an abs newbie and would like to know if it is possible to configure ADSL modem to connect to the net using Live CD 5.10?
Did sudo pppoeconf from terminal and followed all prompts and after finishing typed plog which said that could not connect and " the username or password is incorrect" . I am on XP and when connecting from there the same username and passwords work.Where have I gone wrong?
I'll be thankful for any help.[/QUOTE]

drjaycee - please check with your ISP regarding your username and password. The password and username that you use in winxp is sometimes different than what you require to log-in to their server. I myself have a different username and password when using my pc on M$ and a different one when using Linux.

Your ISP might say that they dont support linux but just ask them for the username and password for your account (not your login name and password).

K

---

### Post by drjaycee on 2005-11-15
Thanks,
Will give it a try and let know.

---

### Post by drjaycee on 2005-11-17
Went to my ISP's web site and located their instructions for "Configuring the ADSL Modem-For Linux/Mac/NT users" and used the specified "Username" and "Password" but to no avail. 
I must point out that I had already done the initial configuration from XP and changed the password immediately thereafter as suggested by my ISP.
(The default password supplied by them was different from the* linux specified* one)
Thankshttp://ubuntuforums.org/images/smilies/confused.gif
:confused:

---

### Post by bulldogzerofive on 2005-11-17
This is just a thought:

A lot of ISPs provide a router as part of the sign up package in my neck of the woods... if yours is the same way, then you should be able to flip through the router's manual, find its address (192.168.something.something), then just open firefox and go straight to that address, then use the router to control your internet connection with the same username and password you usually use.  Even in XP this is a more secure way of doing business anyway.

Hope it helps.

---

### Post by rooster on 2005-11-17
drjaycee, are you from Germany and using T-Online? Then you have to modify your username like this:

> Als T-Online-Kunde erhält man z.B. folgende Personendaten:

    * Anschlusskenung - 000920367867
    * Zugehoerige T-Online-Nummer - 530014442280
    * Mitbenutzernummer/Suffix - 0001
    * Personliches Kennwort - 03387223

Der einzustellende Username setzt sich nun aus Anschlusskennung, T-Online-Nummer, Mitbennutzernummer und dem Zusatz @t-online.de zusammen, also in unserem Beispiel:

Username : [email]000920367867530014442280001@t-online.de[/email]

Als Passwort wird ganz ohne Zusatz das Persönliche Kennwort benutzt:

Password : 03387223
 [from here]("http://www.linuxnetmag.com/de/issue7/m7smoothwall1.html")

Hope it helps...

---

### Post by rooster on 2005-11-17
[QUOTE=bulldogzerofive]This is just a thought:

(...) use the router to control your internet connection with the same username and password you usually use.  Even in XP this is a more secure way of doing business anyway.

Hope it helps.[/QUOTE]

That's right - a router would be far more easy, especially when you have a flatline. But if he can use a modem then he can switch to a router later - he has all the information needed.

---

### Post by bulldogzerofive on 2005-11-21
If you have T-online your router address should be 192.168.2.1, in most cases.  At any rate it is in the owner's manual and all you have to do is type that address in Firefox's address bar.

Let us know if it works

---

