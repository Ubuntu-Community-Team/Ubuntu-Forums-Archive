---
title: "Internet with RASPPPOE"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-11-25
Dear All,

I have finally convinced my parents to switch over from Windows XP/VISTA to Ubuntu and finally after a lot of reluctance they have migrated to Ubuntu. They seem to be overall happy. However there are issues with Ubuntu that needs to be sorted out. I need to help them out soon before they change their mind to start using Windows. 

Back there in Bombay, India, they get internet connection through a CAT5 LAN cable that comes inside the house and gets plugged into the LAN / Ethernet card of the computer. The Computer initially had Windows and the ISP guy installed something called RASPPPOE. Its a protocol that queries available internet services. One has to select the appropriate service and the program creates something like a Dial up networking where in you enter the username and password after which you connect to the internet.

Now with Ubuntu, these ISP guys are clueless. They do not know what to do. I searched through the Ubuntu forum and found out a program called RP-PPPOE which is more or less similar to RASPPPOE. I plan to install it for my folks the next time i go to India for a vacation. 

I installed RP-PPPOE at work here to see, how the program looks like. It seemed that i had to compile the program, which i did. However before compiling, i had to run commands like sudo get-essentials, and later after i installed the RP-PPPOE program, i had to install a package called tk8.5 using Synaptic. 

Now my question is how do i do all this on a computer that does not have any internet connection at all. If i get the program up and running, i can have access to internet. But to get the program running, i need the internet. I can copy the program on a CD and take  it to Bombay. But then how do i get the sudo get-essentials and  tk8.5 package without internet?

Any help from you guys will be greatly appreciated. 

Thanks a lot in Advance.

Kind Regards,
Harry

---

### Post by ItsMitsHere on 2007-11-25
Dear H.

If I have got you correct, u want your parents to connect to internet with a ubuntu box and the internet connection is via some DSL/Cable modem which is of the type PPPoE. If this is the case, you don't need to install anything. Ubuntu comes with a PPPoE connection configuration tool. To connect to internet, do this.

1. Connect the ubuntu box to modem via ethernet cable.

2. Switch on the modem power.

3. In terminal type, **sudo pppoeconf**
This will ask for password, provide it.

4. Now you will come across a blue screen within the terminal window which will detect the ethernet connection and configure the internet connection. Accept default values if you don't know how to do it.

5. After few questions, blue screen will ask for username and password. provide them. these are same username and password that you used to connect from windows xp. they were provided by your ISP.

6. After you have finished the internet will be automatically start on each login (if you have accepted default values).

7. Next time onwards, start internet by typing (in terminal ) **sudo pon dsl-provider** and disconnect by **sudo poff dsl-provider**. To check the internet log file, **sudo plog**. U can also make launchers for these purposes.

8. Enjoy, and do not hesitate to ask.

BTW I m in india as well, ask your parants to call me in case of any trouble! Even STD calls are very cheap now! Ha Ha! :)

Regards,
M.

Edit: Also these instructions are fairly simple. You can forward them to your parents as well with some modifications from your side !!!

---

### Post by cool_penguin on 2007-11-26
Hi there,

Thanks a million for your help and timely feedback. Just one small clarification. Back in Bombay, there is no DSL modem. As i told you, we just get an ethernet cable coming inside the house and that is hooked up to the ethernet card that is inbuilt inside the computer. Anyways, looks like your method is super simple and it should work. I shall forward the instructions to my parents and hope that their ubuntu box is up and running. 

Where in India are you from? My parents are from Bombay. How long have you been using Ubuntu?

Thanks a lot once again.

Keep up  the good work.

Cheers,
Harry

---

### Post by ItsMitsHere on 2007-11-27
Dear H.

I'm in Ahmedabad, Gujarat (If you know where it is ;)). As for how long I have been using linux, I started using it some 2 months back but haven't used it much (totallin about 72 hrs! if that matters...), however, I've been using computers for a long time now. 

I can't use linux continuously 'coz of some platform dependant apps which are not available for linux. Having said that, I love exploring UBUNTU, and thats how i have learned the things!!!

Even if you don't have modem, as long as your connection type is PPPoE (which i'm sure it is), you will manage to connect to internet according to this procedure. Only problem arises when you try to connect through USB instead of Ethernet, 'coz USB modems are not well supported on linux.

Anyways, tell me if everything goes well.

Regards,
M.

---

### Post by cool_penguin on 2007-11-27
Dear M, 

Thanks a million for your help and timely support. I have forwarded your instructions to my brother and parents back in Bombay. (They are all Non-Linux people). I hope that things go well. 

My parents have have internet access through some ISP called Five Network. The network operator has tied-up with a number of ISPs, one of them being Deep Communications (with whom we have an account).

Using raspppoe program in WinXP, you can query the pppoe services being offered on the network, and from the list of services, select the relevant name (Local ISP) to create a dialer. However, since raspppoe is not compatible with Ubuntu, I was wondering if there is any way of finding the names of available services / service providers on the network at any given point of time.

Is there any Ubuntu-compatible software that provides this functionality of finding / querying the pppoe services available on a network?

I shall anyway let you know how things go with my parents. In the meantime, i shall greatly appreciate your feedback on the above question.

Keep up the good work bro. 

Cheers,
Harry

---

