---
title: "Irc? :("
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by igknighted on 2007-03-05
Ok, this is a mildly embarrassing question, but I am completely unfamiliar with how IRC works, any way someone can give a quick tutorial on how to get into the #ubuntuforums-beginner channel?  I just downloaded Konversation, which is what I plan to use (unless someone else has a better client I should try)

---

### Post by bodhi.zazen on 2007-03-05
LOL ~ 

[http://www.irchelp.org/irchelp/irctutorial.html](http://www.irchelp.org/irchelp/irctutorial.html)

In a nut shell ...

Open Konversation

Enter :

/server irc.freenode.net
/join #ubuntuforums-beginner

See the above link to set you nick (name) ...

---

### Post by bapoumba on 2007-03-05
Thread moved to the Absolute Beginner Talk *support* forum ;)

---

### Post by Roger_Melly on 2007-03-08
Uh-Oh....here we go.
It grieves me to say this but despite your best intentions I am a bit lost.

I read the How to as mentioned above which went on and on and is maybe a bit outdated.  I downloaded through synaptic the IRCsci or something similar but goodness knows where this went.

I thought I would keep it simple so looked at Konversation which is for Kubuntu.

I have Gnome and so  I have downloaded and installed Xchat IRC from add/remove.  I then copied the text address to Networks but it wasn't recognised.  What should we Gnome users do?

---

### Post by bodhi.zazen on 2007-03-08
Two options :

1. Install Chatzilla. It integrates with firefox and will get you started.

[https://addons.mozilla.org/firefox/16/](https://addons.mozilla.org/firefox/16/)

[http://www.hacksrus.com/~ginda/chatzilla/faq/](http://www.hacksrus.com/~ginda/chatzilla/faq/)

OK, now click on the irc link ...

OR

fire up chatzilla

In the text box :

/server  irc.freenode.net   <- Watch the space

/join #ubuntuforums-beginners (in the freenode window)

viola

======

#2 Start xchat (should be in your menu)

At the dialog box, select freenode from the list of servers ...

At the next dialog box, select "join a channel" , enter #ubuntuforums-beginners in the adjacent box :)

Note: the above commands work as well :)

/server ....
/join .....


HTH

---

### Post by Ek0nomik on 2007-03-08
IRC is a pretty simple program to use.

Some of the basics:  Port 6667 is the default, and +7000 is for SSL.

Common Commands:

/server irc.NAME.net
/server -m irc.NAME.net (Opens the server window in a new window)
/join #CHANNELNAME
/join #CHANNELNAME OPTIONALkey (If there is a key to the channel)

/msg (Sends messages to users)

If you need to register your nickname:
/msg nickserv register help

If you want to identify yourself after registering:
/msg nickserv identify USERNAME PASSWORD

Some networks have vhost options, which allows you to hide yourself.

/join #vhost is usually the common channel.

Cheers!

---

### Post by Abhi Kalyan on 2007-03-15
Oh My God!!! Am really Sorry!!!!

I meant "I, as in myself" did not have the brain to search in This Ubuntuforum, i was googling all over, and went to lot of other places  to understand IRC.
I did not know how to get in till yesterday.

I seriously did not use it on some body else. and i never mean to hurt any once feelings.

In my excitement i had mistyped.
Am really sorry and will hence forth will take greater care while typing, such that my intentions are not misconveyed.
Thank you for pointing this out.

---

### Post by damu on 2007-03-15
I must say that the IRC protocol is absolutely driving me nuts!


The only way to contact some ubuntu project (I have ubuntustudio in mind)  is IRC, and IRC looks as easy to use for a noob as quantum physics for a frog : every single tutorial that I have seen goes on and on and on about command line and complex issues for which I honestly don't give a stuff. I just want it to work!
I am not interested in command line, and probably will never be. I don't care either if some developers/programmers/advanced users think it is faster, better. I prefer a plain simple GUI!

**bodhi.zazen has offered a 'quick start' solution in 10 lines : thanks for this** . It looks like what a good ubuntu tutorial should be  to me :** simple, efficient, targeted for average users**.

With this help, I could connect to the ubuntustudio channel. But now, I get the message :
> This channel requires that you have registered and identified yourself with the network's nickname registration services (e.g. NickServ). Please see the documentation of this network's nickname registration services that should be found in the MOTD (/motd to display it).

I don't even want to go back to the "Martian speaking'  freenode faqs.
It sadly feels like a bad joke to me:( 

bodhi.zazen, would you have an elegant  solution to my problem which fits in  'few lines' in the "simple, efficient, targeted for average users" spirit ?

thanks

---

### Post by bodhi.zazen on 2007-03-15
> **damu said:**
> I must say that the IRC protocol is absolutely driving me nuts!


The only way to contact some ubuntu project (I have ubuntustudio in mind)  is IRC, and IRC looks as easy to use for a noob as quantum physics for a frog : every single tutorial that I have seen goes on and on and on about command line and complex issues for which I honestly don't give a stuff. I just want it to work!
I am not interested in command line, and probably will never be. I don't care either if some developers/programmers/advanced users think it is faster, better. I prefer a plain simple GUI!

**bodhi.zazen has offered a 'quick start' solution in 10 lines : thanks for this** . It looks like what a good ubuntu tutorial should be  to me :** simple, efficient, targeted for average users**.

With this help, I could connect to the ubuntustudio channel. But now, I get the message :


I don't even want to go back to the "Martian speaking'  freenode faqs.
It sadly feels like a bad joke to me:( 

bodhi.zazen, would you have an elegant  solution to my problem which fits in  'few lines' in the "simple, efficient, targeted for average users" spirit ?

thanks

LOL thanks for the feedback.

Ek0nomik posted the solution, although it may not be obvious :)

To register your nick :

```
/msg nickserv REGISTER <password>
```

Then, when you log into irc identify yourself :

```
/msg nickserv IDENTIFY <password>
```

wher <password> is your desired password (ie do not enter "<password>" but rather something you can remember like "thlw3" )

---

### Post by FyreBrand on 2007-03-16
I've been using Konversation to logon and watch.  It gave me a nick based on my account name.  I guess that's fine.  I wish it wouldn't broadcast my IP and domain host to the world though.  Is that common?  I don't mind having my nick show up but can I hide my IP address?

---

### Post by vincentvee on 2007-08-07
get chatzilla, works with firefox or swiftfox(whick is basically firefox--you can get swiftfox and all the good plugins thru automatix2)
you can get chatzilla [here]("https://addons.mozilla.org/en-US/firefox/addon/16")
[https://addons.mozilla.org/en-US/firefox/addon/16](https://addons.mozilla.org/en-US/firefox/addon/16)
good luck with it.
you could also try installing [seamonkey]("http://www.mozilla.org/projects/seamonkey/"), but i don't know what installation is like under 7.04 and when i had it running uder 6.10 it was not just a matter of getting it through synaptic, there is a thread on the forums about it, but anyway, it installs with a browser, irc client, html editor and maill client, like i said though, i have no idea what the install entails in 7.04, i only use swiftfox

> **Roger_Melly said:**
> Uh-Oh....here we go.
It grieves me to say this but despite your best intentions I am a bit lost.

I read the How to as mentioned above which went on and on and is maybe a bit outdated.  I downloaded through synaptic the IRCsci or something similar but goodness knows where this went.

I thought I would keep it simple so looked at Konversation which is for Kubuntu.

I have Gnome and so  I have downloaded and installed Xchat IRC from add/remove.  I then copied the text address to Networks but it wasn't recognised.  What should we Gnome users do?

---

### Post by jqball2u on 2007-10-14
Thanks [[COLOR=#D40000]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054")!   U  :guitar: !!

Your information is of great value!  I've learned more about how to get IRC up and more about it's workings in the last few hours than I knew several years ago, when I was using Windows 98! :)

I look forward to chatting with you in the future, and to getting to know all of ya'll on this forum!

Usted la Pasta, ya'll! :lolflag:

QBall2U (a.k.a. QBall  [family nickname])

---

### Post by jayaramk on 2007-10-17
i tried to use xchat and also chatzilla to connect to the irc network............ but its not connecting to the server... it still says connecting even waitintg for about 15 min!!!!

---

### Post by bodhi.zazen on 2007-10-17
> **jayaramk said:**
> i tried to use xchat and also chatzilla to connect to the irc network............ but its not connecting to the server... it still says connecting even waitintg for about 15 min!!!!

Just a wild guess, but ...

Are you running a firewall ?

---

### Post by misfitpierce on 2007-10-17
I prefer xchat-gnome myself :)

---

### Post by nikoPSK on 2007-11-26
Thanks for the info and links. Now I need to find a particular client to suit my needs....

---

### Post by harrybazeegar on 2008-01-27
I have been using computers for about a decade but never in my life have i used IRC.

So i tried to get stared... i read that i could use gaim for IRC but when i opened up gaim (i use ubuntu 7.04) It asked me to add usernames and what nots.

I just want someone to guide me in a spoon-feedy, step-by-step way so i can get up and started with IRC... I want to be able to join the ubuntu beginners channel via IRC.

INFO : I am behind a HTTP proxy.. just so u know

Thank you for being detailed, and not alarmingly concise :)

---

### Post by emarkd on 2008-01-27
I can't help you with GAIM because I've never used it for IRC.  However, I recommend Xchat.  It's a great, easy to use IRC client and it's available in the repos.

---

### Post by finer recliner on 2008-01-27
i recommend using Xchat as an IRC client, instead of gaim (now called pidgin)

if you dont already have it installed, you can grab it in "add/remove programs"

it should come with the ubuntu channel already bookmarked so you can jump right in.

---

### Post by harrybazeegar on 2008-01-27
ok... then xchat plz... I just want to be able to chat (do i sound desperate??!)

---

### Post by bodhi.zazen on 2008-01-27
I posted this for people like yourself :

how to irc : [http://www.ubuntuforums.org/showthread.php?t=376907](http://www.ubuntuforums.org/showthread.php?t=376907)

post questions there so as to help others ..

Edit: on second thought I am going to merge these threads ... Look up ^^

---

### Post by harrybazeegar on 2008-01-27
wow... what happended to my thread?! 
great!!!

---

