---
title: "[help!]Thunderbird with webmail doesn't work"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Calvin.Xu on 2006-08-25
I installed Thunderbird and the webmail extension, trying to get access to hotmail, and unless i use "sudo mozilla-thunderbird" to start the application, thunderbird alerts me:"Could not connect to sever localhost; the connection was refused"

It still doesn't work after I added current user to root group.

Anyone has a solution? or anyone has ever encountered the same problem?

---

### Post by riverman on 2006-08-25
> I installed Thunderbird and the webmail extension, trying to get access to hotmail, and unless i use "sudo mozilla-thunderbird" to start the application, thunderbird alerts me:"Could not connect to sever localhost; the connection was refused"

Have you checked your firewall configuration?

---

### Post by Calvin.Xu on 2006-08-25
woo~~,thanks, but I haven't installed any firewall application yet.

So how to change the firewall configuration?

---

### Post by bollix47 on 2006-08-25
What port are you using for POP?

The default 110 for localhost may not work and should be changed to 1025.

This is done in the preferences for the webmail extension and the account settings in thunderbird.

---

### Post by riverman on 2006-08-25
> **Calvin.Xu said:**
> woo~~,thanks,
You're welcome :)

> but I haven't installed any firewall application yet.

So how to change the firewall configuration?

Ah; if you haven't got a firewall installed yet, it's unlikely to be the cause of the problem. But anyway; have a look at [https://help.ubuntu.com/ubuntu/desktopguide/C/networking.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/networking.html") for some info on configuring a firewall using a graphical interface. There's also bound to be some info in the very excellent [Unofficial Ubuntu Starter Guide]("http://ubuntuguide.org/wiki/Dapper"). If it's not your firewall that's causing the problem, I'm probably not going to be able to help - sorry :(

Incidentally, are you connecting to the net directly from your Ubuntu box, or through a router/server?

---

### Post by Calvin.Xu on 2006-08-25
> **bollix47 said:**
> What port are you using for POP?

The default 110 for localhost may not work and should be changed to 1025.

This is done in the preferences for the webmail extension and the account settings in thunderbird.
I changed the port for POP to 1025 and it still doesn't work:((

and I install firestarter and even after I chose to stop the firewall, thunderbird still tells cannot connect to localhost.

---

### Post by Calvin.Xu on 2006-08-25
> **riverman said:**
> You're welcome :)



Ah; if you haven't got a firewall installed yet, it's unlikely to be the cause of the problem. But anyway; have a look at [https://help.ubuntu.com/ubuntu/desktopguide/C/networking.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/networking.html") for some info on configuring a firewall using a graphical interface. There's also bound to be some info in the very excellent [Unofficial Ubuntu Starter Guide]("http://ubuntuguide.org/wiki/Dapper"). If it's not your firewall that's causing the problem, I'm probably not going to be able to help - sorry :(

Incidentally, are you connecting to the net directly from your Ubuntu box, or through a router/server?
thanks all the same.

and i think i'm connecting to internet through a gateway.May that cause the problem?

---

### Post by Calvin.Xu on 2006-08-25
but i could make it work by using "sudo mozilla-thunderbird" to start the application, so I guess it might be the problem of current user's privilege

---

### Post by riverman on 2006-08-25
> and i think i'm connecting to internet through a gateway.May that cause the problem?
I'm not sure to be honest with you; maybe someone else can give some advice on that?

> **Calvin.Xu said:**
> but i could make it work by using "sudo mozilla-thunderbird" to start the application, so I guess it might be the problem of current user's privilege
Maybe true. It seems strange, though, since ordinarily you'd be using Thunderbird with your usual privileges anyway: it *should* work...

---

### Post by Calvin.Xu on 2006-08-25
actually, i can use thunderbird to access my gmail account, so i guess it's the problem with "localhose" rather than thunderbird.

Anyway, thanks a lot!

---

### Post by riverman on 2006-08-26
> **Calvin.Xu said:**
> actually, i can use thunderbird to access my gmail account, so i guess it's the problem with "localhose" rather than thunderbird.

Anyway, thanks a lot!

Glad you've got something working. 

If you do still feel like hacking away at Hotmail, my one final thought is this. If you are connecting through a gateway, you might need to change the Thunderbird/webmail extension connection settings to make sure Thunderbird is using the correct connection. Unfortunately, I can't tell you how to do this, because I don't use Thunderbird - sorry :) I'd imagine it's done in a similar fashion to what bollix47 advised earlier:

> 
What port are you using for POP?

The default 110 for localhost may not work and should be changed to 1025.

**This is done in the preferences for the webmail extension and the account settings in thunderbird.**(my emphasis).

Happy emailing!

---

### Post by msak007 on 2006-08-26
Well I assume that along with the actual WebMail extension, you also installed the needed extension(s) for Hotmail / Yahoo (or whatever else you're using). When you check the WebMail extension's preferences, what is the status of the localhost server (in the Servers --> Status tab)? You should see 3 entries for POP, SMTP, and IMAP that should be green if the service is running, red if it's stopped, or black if it's not enabled.

---

### Post by qpieus on 2006-09-07
> **Calvin.Xu said:**
> I changed the port for POP to 1025 and it still doesn't work:((

and I install firestarter and even after I chose to stop the firewall, thunderbird still tells cannot connect to localhost.
I had the same exact problem as you. I changed the port to 1025 in BOTH the webmail preferences AND the hotmail/yahoo/whatever account settings (click Account Settings in the Edit menu, then click on Server Settings.
Did you change BOTH places to port 1025?
I changed both places and now I can check my yahoo email via thunderbird.

---

### Post by jediborger on 2006-09-07
I had the same and I know how to fix it. First set up the webmail extension to use port 1025 for the POP email and the others for ports 1026 and 1027 if neccessary. Then install the extensions you need for your accounts Yahoo, etc. Now create your account and when it asks for server type localhost and when it asks for username type *username@domain.com* make sure you do that otherwise it won't work. Then under the server settings after you create the account you need to set the port to the same number as what it is in the webmail config. For example my Yahoo acount uses POP and webmail has as 1025 so under the serer setting for my Yahoo account it has to 1025. Now it should work fine.

Note: The Yahoo extension doesn't work with the new mail beta so make sure you're stilling using the old version of Yahoo mail.

Also the reason you got gmail to work is because google provides a regular pop account for all it's google accounts, so you don't even need this extension to use gmail with Thunderbird.

Hope this helps, it took me a while to figure it out and also check out the documentation at [http://webmail.mozdev.org/setup.html]("http://webmail.mozdev.org")

---

### Post by BrianAT on 2006-09-29
Just in case it will help others, 
I was having a simular problem. Under the Servers Status all three have green lights. The Gmail extention is listed as active. However, when I click Add New Account, I see no web mail option.
If I use
```
sudo mozilla-thunderbird
```
I do see the option.

To fix it, I right clicked Applications and chose Edit Menus. There I found Thunderbird (under Internet), right clicked it and chose properties. Edit the command so it has the sudo command in front of it like the code box above. I closed that box, then found Thunderbird in the main menu and right clicked it from there to add it to the pannel and it kept the sudo in front of the launch command.

---

### Post by AmandaKerik on 2007-02-01
> **Calvin.Xu said:**
> I changed the port for POP to 1025 and it still doesn't work:((


Where did you change the port - in the account settings or in the webmail preferences.

Change it in the add-on, then change the account settings to match ;)
Tools > Extensions > Webmail > Preferences > Servers > Ports
Change it to something like 1111 and 1112 or whatever you prefer
Restart Thunderbird then check for green lights in:
Tools > Extensions > Webmail > Preferences > Servers > Status

Hope this helps,
Amanda

---

### Post by Paqman on 2007-02-07
Excellent, I was having this exact problem. Setting the port to 1025 worked no problem!

---

### Post by sk545 on 2007-08-28
So, pop is set to port 1025, but what do we set the SMTP to?  Should that be left as port 25?

---

### Post by eneth80 on 2008-02-27
great, finally it works!! thanks a lot! 
tow question: once I have 'seen' my emails in thunderbird are we sure the emails will stay in yahoo? I have had some bad experiences with POP in the past, I do not want to lose the emails I have in my yahoo account! For the moment this is not the case.
and to send an email? i cannot put smtp to the same port as pop.
thanks
ale

---

