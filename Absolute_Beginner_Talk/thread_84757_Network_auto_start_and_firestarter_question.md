---
title: "Network auto start and firestarter question"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by BizzyLizzy on 2005-10-31
Hi hope someone can help me.

Every time I restart the linux box my two network cards do not automatically activate.  This means in turn that firestarter cannot autostart.

The trouble is that where we are based we currently have a fair few power outages which mean that the box reboots and then I have to manually logon to the desktop and start the network adapters and then start firestarter.

Is there anyway to auto start the network cards on boot up and auto start firestarter on boot up as well.

Thanks

Lizzy

---

### Post by Kapre on 2005-10-31
[QUOTE=BizzyLizzy]Is there anyway to auto start the network cards on boot up and auto start firestarter on boot up as well.
Thanks
Lizzy[/QUOTE]

Lizzy - I would like to help you on how you can autostart Firestarter.....Go to System---->Preference----->Sessions------>select the third Folder (Startup Programs)-----then click on Add----->keyin firestarter at the Startup Command then click OK...then close.

K

---

### Post by BizzyLizzy on 2005-10-31
Hi thanks for the quick reply.

I have done as you suggested - unfortunately the problem is that when I reboot the network cards do not automatically activate and that then means that firestarter cannot and is not automatically starting up.

Any more suggestions?

Lizzy

---

### Post by Samuel on 2005-10-31
not sure how to fix this but i stopped using firestarter because of similar problems at boot time, it didnt seem to like vmware, 
i dropped firestarter for ipkungfu and im happy with it. its no gui but if you read the instructions its a doddle to set up

---

### Post by BizzyLizzy on 2005-10-31
Thanks Samuel

but I think that installing a diff firewall is not really going to solve my problem.  Wont matter which firewall I am using if the network cards wont start on boot up :(

Cheers Lizzy

---

### Post by BizzyLizzy on 2005-10-31
Right I have been doing a bit of digging around.  I have found that on boot up or shutdown there is a process failing.  Process 'Configuring network interfaces' shows as 'fail' and similarly on shutdown 'Deconfiguring network interfaces' shows as 'fail' as well.

This probably explains why the cards are deactivated when I reboot the machine and have to restart them manually.  So can anyone tell me where the problem is or where to start looking.

Cheers

Lizzy

---

### Post by BizzyLizzy on 2005-10-31
Come on ppl - someone out there must have some idea whats wrong with my system.  Have I configured something incorrectly?  Trouble is I have absolutely no idea where to even start looking :(

---

### Post by BizzyLizzy on 2005-11-01
Hellllpppp - I cant believe that there is no one out there who does not have at least some idea of where to look to fix my problem. 

Please help me someone I am desperate.

:(

---

### Post by BoyOfDestiny on 2005-11-01
[QUOTE=BizzyLizzy]Hi hope someone can help me.

Every time I restart the linux box my two network cards do not automatically activate.  This means in turn that firestarter cannot autostart.

The trouble is that where we are based we currently have a fair few power outages which mean that the box reboots and then I have to manually logon to the desktop and start the network adapters and then start firestarter.

Is there anyway to auto start the network cards on boot up and auto start firestarter on boot up as well.

Thanks

Lizzy[/QUOTE]

What kind of power outages... I know this isn't a real solution to your question, but it might be a workaround. 
Have you considered investing in an UPS (uninterruptable power supply). Think of it as a battery for your computer. If you just have brown outs (very short blackouts) it would prevent your machine from going down. 
Depending on the model and how much juice your computer uses, you could have it running from 20min to over an hour without power...

---

### Post by BizzyLizzy on 2005-11-01
:smile:  Thanks for that!! the power outages are a mixture of brownouts and full blown power cuts.  We are in the process of putting a UPS in, but as you say doesnt really solve the problem.  

I would really love to know why the network cards are not starting up automatically. 

Surely someone out there must have a clue!

Cheers Lizzy

---

### Post by GreyFox503 on 2005-11-02
It sounds like you know how to enable the networking and start the firewall, but you have to do it manually each time you start up.

If you can figure out the terminal commands to accomplish these tasks, you could put them in a script to do them automatically for you.

---

### Post by BizzyLizzy on 2005-11-02
lol well thanks for that!!  I am a complete linux newbie so knowing what or even how to put the commands in a script would be a fine thing!!

:smile:

---

### Post by GreyFox503 on 2005-11-03
It's not too hard.  Here's some examples to start looking at:

[http://www.tldp.org/LDP/abs/html/sha-bang.html](http://www.tldp.org/LDP/abs/html/sha-bang.html)

If you just want to start small, its a plain text file (made executable) that has a list of commands executed one-at-a-time.  You can make more advanced scripts, but a small one can be written very easily.

---

### Post by BizzyLizzy on 2005-11-03
Thanks for the link Grey - I will have a read when I get back into the office.  

Now all I need to do is to find the commands for starting up the network cards!! :smile: 

Lizzy

---

### Post by GreyFox503 on 2005-11-04
[quote=BizzyLizzy]
Now all I need to do is to find the commands for starting up the network cards!! :smile: [/quote]

And therein lies the crux of the problem.  This has happened to me sometimes.  Sometimes I wish Ubuntu wouldn't make things so easy for me.  :)

There are a few things I do in the GUI that take me a while to figure out the equivalent commands for.  I believe that anything you can do point-and-click, you should be able to do at the terminal as well.  Because as far as I know, you can't script mouse clicks.

---

