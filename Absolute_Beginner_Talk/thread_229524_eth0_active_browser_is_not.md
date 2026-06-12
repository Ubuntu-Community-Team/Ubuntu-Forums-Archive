---
title: "eth0 active/ browser is not???"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by dad_e_man on 2006-08-04
:confused: I cannot surf. :-({|=  Ubuntu loads just fine, but when I try to browse all I get is "the page cannot be displayed"  So as part of my troubleshooting goes I decided to set up a static ip instead of DHCP..  still no go..  etho is active.. packets are being sent and recieved..   but my browser doesn't seem to think so..   so next I try my other router(I have two) just to see if maybe its yet another Linksys problem...   but no, the motorola tells me the same story.  Please tell me someone can help me.:confused:

---

### Post by Tomosaur on 2006-08-04
Which browser are you using, and do you have any problems with other internet-dependant activities?

---

### Post by dad_e_man on 2006-08-04
such as??  and as far as browsers go I have tried Firefox only.

---

### Post by steve.horsley on 2006-08-04
My guess is that it doesn't know the default gateway (your router) to send its packets to. To check this, can you post the output from the command **route** ?

Do you know the IP address of your router? If not, you may need to configure DHCP adn run the route command again so that you can see what the default route should be.

---

### Post by Tomosaur on 2006-08-04
> **dad_e_man said:**
> such as??  and as far as browsers go I have tried Firefox only.

Open the synaptic package manager (Click Applications, then Add/Remove) and try downloading a program.

---

### Post by dad_e_man on 2006-08-04
Sorry, I guess I could give you more details huh? As far as trying any other web based applications go, No, I have not tried any.  I pretty much stopped right away and banged head into wall..  then rinsed and repeated. I have had this problem on this particular comp several times w/ Linux (various distros) and I just don't get it.  I have pretty much eliminated the possibility of it being a router configuration or problem, due to the fact I have Suse up and running on an older comp that I gave my step daughter.  Both are set up identically...  (well of course the ips are different) but you know what I mean..  I did nothing different when I installed. I am in winblows at the moment and any advice given will take me a moment to attempt.. so bare w/ me please and I just want to say thanks for the speedy reply.  Let me know what other information you may need.

---

### Post by dad_e_man on 2006-08-04
I am new to linux...  but I am thinking I don't download in the traditional manner (winblows click and execute) So tell me..   how do I download?  Doesn't it require a command of some sort?  (Sorry for my brand newbian questions)

brb.. gonna go see

---

### Post by dad_e_man on 2006-08-04
Tomosaur,
"failure to resolve ubuntu archive"

steve.horsley,
as far as my router goes...    when I set up a static ip I have to enter a default gateway.  So shouldn't that take care of that?
And I have tried both by the way..  DHCP and Static, neither work
although I don't recall inputting DNS. Don't even remember seeing a place to do so.  Going to check that now...  kill some time till you get back.

---

### Post by steve.horsley on 2006-08-05
The DNS config goes in /etc/resolv.conf. You could compare yours with your daughters.

Try these commands and post the results:
[B]ifconfig
route
ping 147.83.195.18
ping [www.ubuntu.org](www.ubuntu.org)
[/B]
Can you ping your local router/default gateway?

---

### Post by kurniawands on 2006-08-05
> **steve.horsley said:**
> The DNS config goes in /etc/resolv.conf. You could compare yours with your daughters.

Try these commands and post the results:
[B]ifconfig
route
ping 147.83.195.18
ping [www.ubuntu.org](www.ubuntu.org)
[/B]
Can you ping your local router/default gateway?

or see system > networking > find DNS on it's menu tab, configure it... and it's supposed to solve the problem, if everything is OK. (IP setting and card is recognized/works well)

---

### Post by dad_e_man on 2006-08-07
hey sorry for the couple day delay...   haven't had much personal time lately...   but I'm gonna try again later tonight.. and I'll get back with you tomarrow and post my results...   like I said sorry for making ya wait...    I appreciate all the help...  you all are the best

---

### Post by dad_e_man on 2006-08-08
Before trying the commands I went ahead and tried connecting through the modem.  I made sure that it established connection in windows before returning linux. I got the same results.  It will NOT connect via LAN or modem in Linux but I'm having no trouble connecting in windows. Now I will try the commands and I will be back to post my results.

---

### Post by dad_e_man on 2006-08-08
Ok, you will have to excuse my not having every detail..  I burned some screenshots to disc but apparently the format is not supported.  As far as *ifconfig* on either static or DHCP...  0's all the way across the board on everything except dropped(719 give or take a few)  As far *route* the only way my router and gateway show up at all is to asign it statically(in which case I do see the correct information).  On DHCP *route* is drawing blanks...   and no matter what I ping on either configuration, static, or DHCP, the host is unreachable.  No matter how I have it set up I cannot establish a connection whether using a router or a modem, Static or DHCP, default or adjusted.  And I had this problem on this comp with another distro before discovering Ubuntu. All I can figure is it has to be this Nvidia ethernet card.  I am all out of ideas.  I hope this helps, and I want to again say thank you for your help. Just let me know if you have any more suggestions.[-o<

I very seriously doubt this has anything to do w/ it but this is a fairly new machine all together (purchased on 2/05/06)  just in case I have some sort of alpha driver getting in my way I figured I would mention that.

---

### Post by dad_e_man on 2006-08-08
no clues so far???    that figures, thats the way my cookies crumble..  :-({|=

---

### Post by dad_e_man on 2006-08-18
could it be NVIDIA ActiveArmorTM preventing it?:-k

---

### Post by seshomaru samma on 2006-08-18
> **dad_e_man said:**
> Ok, you will have to excuse my not having every detail..  I burned some screenshots to disc but apparently the format is not supported.  As far as *ifconfig* on either static or DHCP...  0's all the way across the board on everything except dropped(719 give or take a few)  As far *route* the only way my router and gateway show up at all is to asign it statically(in which case I do see the correct information).  On DHCP *route* is drawing blanks...   and no matter what I ping on either configuration, static, or DHCP, the host is unreachable.  No matter how I have it set up I cannot establish a connection whether using a router or a modem, Static or DHCP, default or adjusted.  And I had this problem on this comp with another distro before discovering Ubuntu. All I can figure is it has to be this Nvidia ethernet card.  I am all out of ideas.  I hope this helps, and I want to again say thank you for your help. Just let me know if you have any more suggestions.[-o<

I very seriously doubt this has anything to do w/ it but this is a fairly new machine all together (purchased on 2/05/06)  just in case I have some sort of alpha driver getting in my way I figured I would mention that.

you don't need a screenshot , just type these commands into the terminal and copy the output to a text editor, you will find one in accessories
If you are posting from a windows computer , I think windows can read a text file , if not you can alway upload it in your post (just look for 'attach files' under the Submit reply botton)
I think the output will be very helpful for finding a solution
If you have a Suse machine connected to the same router try to run the same commands as well and post them. Thank you.

---

