---
title: "HOTMAIL....again.."
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by masalf on 2008-03-20
I am sorry to bother with such old question. 
I followed all the steps suggested to have hotmail working on evolution mail

there is a step that stop....
when they say : ***sudo gedit /etc/inetd.conf - ***
then the system open a new windows, empty, and I get completely lost since the next step should be :
- quote -[B][I] 
Look for a line like this:
Code:
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd[/I][/B]
-unquote- 
a this point I get lost.... what/where/how I should proceed and look for this code?

---

### Post by abben on 2008-03-20
> **masalf said:**
> I am sorry to bother with such old question. 
I followed all the steps suggested to have hotmail working on evolution mail

there is a step that stop....
when they say : ***sudo gedit /etc/inetd.conf - ***
then the system open a new windows, empty, and I get completely lost since the next step should be :
- quote -[B][I] 
Look for a line like this:
Code:
pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd[/I][/B]
-unquote- 
a this point I get lost.... what/where/how I should proceed and look for this code?

it looks like the file you were supposed to edit does not exist.

---

### Post by Tom--d on 2008-03-20
I thought Hotmail doesnt support POP? 

Thats why I changed to GMX. Its free and works perfectly in Thunderbird. I did spend ages trying to get Hotmail to work but nothing worked. :(

---

### Post by perlluver on 2008-03-20
```
sudo gedit /etc/inetd.conf - 
```

Might try taking that trailing dash off of there.  I don't think that should be there.

---

### Post by stchman on 2008-03-20
> **Tom--d said:**
> I thought Hotmail doesnt support POP? 

Thats why I changed to GMX. Its free and works perfectly in Thunderbird. I did spend ages trying to get Hotmail to work but nothing worked. :(

Hotmail supports POP on a pay account.  The free ones don't have it unless they are really old.  The really old free ones M$ probably has not gotten around to disabling POP access.

Ubuntu has a package called freepops that will allow you to get your hotmail off of a free account.

---

### Post by scramasax on 2008-03-20
> **stchman said:**
> Ubuntu has a package called freepops that will allow you to get your hotmail off of a free account.

Since Hotmail's a webmail service, the program is presumably scraping the HTML page, which it's getting over HTTP, and then pushing it to the email client over port 110, where POP3 mail would usually come.

It seems a fuss to me.  Gmail has free IMAP access, not just POP.  And it's secure over SSL, too.  Of course, you have to accept that Google will be scanning your mail for the purpose of beaming ads at you (which you'd get in the web interface).  But then MS will be doing the same with Hotmail ...

---

### Post by philinux on 2008-03-20
I have a hotmail account and use TB with the WEBMAIL / HOTMAIL addon.

Works a treat.

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by stchman on 2008-03-21
> **scramasax said:**
> Since Hotmail's a webmail service, the program is presumably scraping the HTML page, which it's getting over HTTP, and then pushing it to the email client over port 110, where POP3 mail would usually come.

It seems a fuss to me.  Gmail has free IMAP access, not just POP.  And it's secure over SSL, too.  Of course, you have to accept that Google will be scanning your mail for the purpose of beaming ads at you (which you'd get in the web interface).  But then MS will be doing the same with Hotmail ...

I have a Gmail account and to tell you the truth I prefer Hotmail's interface.  I have had that account for a very long time.  Gmail's interface seems a bit dumbed down to me.

---

### Post by durand on 2008-03-21
I switched to gmail just because they stopped free POP access. And now gmail for me works perfectly! I just use opera as a POP client.

---

### Post by iheartubuntu on 2008-03-21
I use Gmail and Evolution because gmail offers free IMAP which allows you to view what you have online, offline. Plus it makes it easy to store all your stuff offline if you wish. I hardly log into my gmail account anymore, so who cares about their interface. 

Evolution Mail also is integrated into Ubuntu and Ubuntu calendar which is GREAT. I dont think Thunderbird can do that.

---

### Post by masalf on 2008-03-23
there is no dash in the code... but I found out that now hotmail keeps not working and I got a funny digital voice that run each time I switch on my computer. this funny and noisy voice reads all possible languages available for the ORCA's supports.
how I can stop this voice and have hotmail working?

thank you to all

---

### Post by durand on 2008-03-23
Try turning off assisstive technologies in the preferences: System > Preferences

---

### Post by oldos2er on 2008-03-23
> **masalf said:**
> I am sorry to bother with such old question. 
I followed all the steps suggested to have hotmail working on evolution mail

there is a step that stop....
when they say : ***sudo gedit /etc/inetd.conf - ***
then the system open a new windows, empty, and I get completely lost since the next step should be :
- quote -[B][I] 
Look for a line like this:
Code:
pop3        stream    tcp    nowait    nobody    /usr/sbin/tcpd /usr/bin/hotwayd[/I][/B]
-unquote- 
a this point I get lost.... what/where/how I should proceed and look for this code?

 Use "gksudo gedit" in place of "sudo gedit," since gedit is a graphical program.

 Just checked my /etc/inetd.conf, and it appears the file exists but is empty. Which version of Ubuntu are you running, and how old are the instructions you're following?

---

