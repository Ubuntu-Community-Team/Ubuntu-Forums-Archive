---
title: "Connecting to a wireless connection in school"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by bzzzzz on 2008-03-31
I'm a teacher and linux newbie.  I'm trying out Edubuntu and if I can use it succesfully I will try to use it more extensively within the school.

I realise that I could spend a long time searching through the forums trying to find a solution for my problem, but unfortunately I can only test ideas when I'm in school and I cannot afford a great deal of time to test things.

I am using edubuntu installed using wubi on a dell latitude d505 laptop.
My problem is that the computer finds the schools wireless network, but I cannot open any web pages  using firefox.  

I can use the laptop at home with my own wireless connection and connect with both ubuntu and xp.  At school I can find the internet connection using xp.  I have to go to"advanced settings" and adjust the "settings" so that I connect to the "Manual proxy configuration" 192.168.0.4 port 8080.  

With Ubuntu I do the same things in firefox and I find the network but cannot open web pages, it just says that I should check the proxy settings.

I realise that my explanation is a bit long winded but I'm hoping the fix will be short and sweet.

---

### Post by abhiroopb on 2008-03-31
can you test and see if skype or pidgin works? Otherwise go into firefox Edit>Preferences>Advanced Tab>Network Tab>Settings

Select Manual Proxy Configuration, and set HTTP: 192.168.0.4 port: port 8080. Save, exit and restart firefox.

---

### Post by dstew on 2008-03-31
You may need to set the http_proxy environmental variable. Open a terminal and enter:```
export http_proxy="http://192.168.0.4:8080/"
```if that is the correct IP for your proxy server.

---

### Post by bzzzzz on 2008-03-31
I've tried both of those - the first is how a successfully connect to the internet using firefox and xp, but fails when I'm using Ubuntu.

The second did not work.

I'm willing to try other ideas.

---

### Post by Fire_Chief on 2008-03-31
Can you connect to local resources on your school network (printer, file server, etc)? If not, you may not be getting an IP from your wireless connection.

---

### Post by bzzzzz on 2008-04-01
I can't get those things.  usually when i want to look at something over the school network i am askedfor my password, however in edubuntu although it finds (and says its connected) the wireless connection I don't get asked for my password.

---

### Post by abhiroopb on 2008-04-01
are you asked for your password in a pop-up box? which says username and password?

---

### Post by Xiong Chiamiov on 2008-04-01
I suppose that it's possible there's some sort of access restriction software, like the god-awful cisco clean access they use at my school.

---

### Post by abhiroopb on 2008-04-01
have you tried using a vpn (virtual private network), perhaps its offered at your school?

---

### Post by rimmer74 on 2008-04-01
Are you sure that is your proxy server or just the main computer server in your school?  The proxy server in my school is proxy.swgfl.org.uk which i type into the manual proxy configuration menu. Yours will depend on who provides your school internet access.

Also once you've got it working you may want to use FoxyProxy add-on to switch between the proxy and non-proxy if you use it at home.

I too am desperately trying to get Linux talking to all my network devices etc so we can free ourselves from the shackles of W**dows. Good Luck!!

---

### Post by jw5801 on 2008-04-01
You'll need to talk to the IT guys at your school. Is your XP install set up by them, or is it a stock standard install? It sounds as though you may need a VPN or something similar. Have a look at the output from "iwconfig" when you're connected and make sure you've been given a proper IP and all that sort of stuff.

---

### Post by bzzzzz on 2008-04-01
I do get a pop up saying username and password when I access the internet using xp, but it does not happen when I'm using Edubuntu.  

I believe that the proxy is correct because this is what I use when using xp, and I have a friend who uses a mac and finds that he can connect to the internet without any problems.

---

### Post by bzzzzz on 2008-04-01
The IT guys will just say "use xp, what's the problem?"

---

### Post by abhiroopb on 2008-04-01
I think the issue with edubuntu is that this pop is not coming. For example when I log into my university group mail, in XP I get a pop up for username and password, and in ubuntu I get it as well. Not sure why but you should be getting this. Otherwise you'll need to login with a VPN (which without help will be quite difficult to achieve).

---

### Post by MONODA on 2008-04-01
i cant believe no one else said this:
if you right click (or left click, I dont remember) on the network icon, you should be able to select manual configuration and input the proxy and port.another way is to go: system->administration->network and to select properties on the network you want to configure and configure it from there.

---

### Post by bzzzzz on 2008-04-01
I've posted the network proxy in just about every place its possible to - but no cigar to date.

---

### Post by bzzzzz on 2008-04-02
Okay this may help.

I've managed to connect in xp using firefox and explorer.  When connecting using explorer I have to do something a little different to the way I do it in firefox.

I go to Tools => Internet options  then click LAN settings, then I tick the box Use a Proxy for your LAN and I click the _bypass proxy server for local addresses_

I wonder if this is relevant, and is there a way to do this in firefox.  I'm wondering if the setting is automatic in xp, but I need to change something when using firefox in ubuntu.

---

### Post by bzzzzz on 2008-04-04
I took my laptop to school again and this time tried to connect to the internet in the same way using opera.  To my surprise it worked!

I then tried using firefox and inexplicably firefox now connects.  Go figure? :)

Only one more thing that needs clearing up.  Firefox asks for my password 4 times before letting me connect, whereas opera only asks me once.  Is there any change in settings that I can make which will allow firefox to just ask me once?

---

### Post by dwally89 on 2008-04-04
In my school it asks me for my username and password a few times too. Have not found any way to get around it.

---

### Post by abhiroopb on 2008-04-04
Perhaps try using a master password in firefox?

---

### Post by ibgeorgeb on 2008-04-04
I'm having the same issue with Ubuntu 6.10. My toshiba laptop used to logon to the internet with not problems (using a blue colored cable) --up to three weeks ago. Now, I'm getting the "Access Denied" and to logon using the user.name and pass.word menu. But there is no user.name and pass.word  menu. Yes; this is at elementary school. Our district uses Barracuda Network to, I guess, control our access to the network. Our network administrator advised me via memo today to buy a windows computer that'll work with our district's network. 
     I'd sure like to know what worked with buzzzzzzzz that got the username and password menu to appear. In the meantime, I'll try some of your ideas come Monday morning if I can find the time during the day at school. Cheers, ibgb

---

