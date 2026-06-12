---
title: "bios problem"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by balticman on 2007-12-03
After a month of dual booting my PC (Aspire T120) now only gets as far as the CMOS set up screen. After having read some other threads I have done the following-

1. Tried to boot from a a Live CD . Nothing happened.

2. Tried to remove the CMOS battery. Could not remove but maybe if I forced it?

3. Reset the 1 RAM stick to the other slot. No change.

4. Both fans are working correctly

5.I have set the CMOS settings back to default.Nothing changed.

6. I cannot identify the beeb code. MY bios is Phoenix and it makes a sound like 5 or 6 beeps together.But its difficult to be exact.

7. On my last attempt to restart I noticed the date was wrong in the CMOS settings. I could change the time and year ie.the numeric values ,  but not the month. 


I dont know anything about the other CMOS settings.The fans run very quickly but I think thats normal during booting. It seems my hard drive is detected. 

Has anyone got any ideas of other possible approaches ? 

Thanks in advance.

---

### Post by daimaru on 2007-12-03
go to a hardware store and have your pc checked... either your ram is busted or your motherboard.

---

### Post by bigken on 2007-12-03
this might help

[http://www.bioscentral.com/beepcodes/phoenixbeep.htm](http://www.bioscentral.com/beepcodes/phoenixbeep.htm)

---

### Post by Don1500 on 2007-12-03
> go to a hardware store and have your pc checked... 

Would ACE be good, or should he go to Home Depot?

Can you boot to Windows? If so, you can download the BIOS from online and install it again. Go to the Pheonix home page, then follow the instructions (look for the download page). If you're sending questions to this forum you are on line, so you may be able to do this.

---

### Post by bigken on 2007-12-03
do you or can you borrow another stick of ram ?


this could be a bad cecksum error pulling the cmos battery would correct it I doubt its the ram or cpu as you would not be able to enter the bios

---

### Post by daimaru on 2007-12-03
> **Don1500 said:**
> Would ACE be good, or should he go to Home Depot?
lol i don't know your american stores so i know that "hardware store" probably wasn't the right choice of words, but you can't allways assume that everyone in the world lives in the USofA. so excuse my vagueness. but i bet he got the point. have your computer checked "somewhere".

EDIT: @balticman 
of course i might be totally wrong here, but i would do that to rule out any hardware problems. which by the way is a service free of charge here in europe :)

---

### Post by balticman on 2007-12-04
I cant boot into windows . I have tried using the XP cd and several live Linux distros. 

I am going to look at the Phoenix site again to see if there is any help there . I have been unable to identitify the beep code. Its like 5 or 6 rapid beeps...but nothing like I can see on the codes.

Failing that I will take the PC to be looked at. I live in Sweden so its going to be expensive. Its may be more economical to just buy a new PC as I dont think I will be able to change the motherboard myself.

Thanks for your replies.

---

### Post by zabien1970 on 2007-12-04
Can you post the make and model of your motherboard? What kind of computer is it installed in

---

### Post by bigken on 2007-12-04
is it 5 or 6 beeps saying its 5 or 6 does not help you or anyone else to try and identify the code is there any gaps between the beeps ? :confused:

---

### Post by balticman on 2007-12-04
It beeps 6 times in rapid succession. No gaps and no beep longer than another.Its really hard to count them as they are so close together.

I have been convinced from the replies that its sometype of hardware fault. It cant be anything to do with the OS. Or can it? Can Ubuntu (or any other OS ) corrupt the bios?

F-spot hung my machine a couple of times and the only way to turn off the machine was to pull the plug.

---

### Post by balticman on 2007-12-04
I think I have identified the problem. After writing "hardware fault" in my last post I thought back to the problem I had entering the correct month in the bios settings. I then restarted the PC without the keyboard plugged in. 

It booted perfectly. When I plugged the keyboard back the PC started beeping like crazy. So either its a broken keyboard or jackpoint that no longer functions. Maybe that what the original beeps meant. I just could not find any refererence to them.I am going to buy a new keyboard to check my theory.

Thanks to everyone for replying.

---

### Post by bigken on 2007-12-04
pleased you found the problem i would buy a usb keyboard at least if its the ps2 port on the board thats faulty usb will get round this

---

### Post by Bartender on 2007-12-04
balticman -
Reminds me of a similar incident.  I work at a coal-fired power plant.  The PC's are shared by a bunch of people.  The keyboards get very dirty with coal dust and food.  It's easy to find another keyboard laying around so I stuck one of them in the sink and washed it.
The PC let me know I'd screwed up by beeping just like you describe.

Now I disassemble the keyboard.  Generic keyboards open up so that I can wash the entire keypad and front bezel while setting aside the back half with all the electronic parts.  Works much better that way!

---

### Post by februarius on 2007-12-04
> **balticman said:**
> After a month of dual booting my PC (Aspire T120) now only gets as far as the CMOS set up screen. After having read some other threads I have done the following-

1. Tried to boot from a a Live CD . Nothing happened.

2. Tried to remove the CMOS battery. Could not remove but maybe if I forced it?

3. Reset the 1 RAM stick to the other slot. No change.

4. Both fans are working correctly

5.I have set the CMOS settings back to default.Nothing changed.

6. I cannot identify the beeb code. MY bios is Phoenix and it makes a sound like 5 or 6 beeps together.But its difficult to be exact.

7. On my last attempt to restart I noticed the date was wrong in the CMOS settings. I could change the time and year ie.the numeric values ,  but not the month. 


I dont know anything about the other CMOS settings.The fans run very quickly but I think thats normal during booting. It seems my hard drive is detected. 

Has anyone got any ideas of other possible approaches ? 

Thanks in advance.

maybe this could help

1. check cmos boot priority
2. put ur hdd ide to secondary then cd rom on master

---

### Post by bobyy on 2007-12-04
I found this 
> 6 Short Beeps  	The chip on your motherboard that controls your keyboard (A20 gate) isn't working. First try another keyboard. If it doesn't help, reseat the chip that controls the keyboard, if it isn't soldered in. If it still beeps, replace the chip if possible. Replace the motherboard if it is soldered in. 

this is the link
> [http://www.pchell.com/hardware/beepcodes.shtml](http://www.pchell.com/hardware/beepcodes.shtml)

---

### Post by balticman on 2007-12-04
Great point about the usb keyboard. I am definatley going to get one just in case the port is dead.

-switches to philisophical mode- I guess the answer was on the net all the time. Hopefully I would have found it eventually. Using this forum though has saved me a lot of time plus I have learned what it is exactly a bios does.Thanks everyone.-philisophical mode off

---

### Post by Don1500 on 2007-12-04
Changing the Mother Board is not really hard. Just watch where you pull things off of(wires, Pluges) , know what they are, and put them back where the (Mostly useless) documentation tells you to. About the only part of the documentation that is consistantly somewhat usefull is the board map. Should only take about 1/2 hr. Oh yess, either make sure your new MB takes the same uProcessor, or buy a new uP and memory at the same time. That will save multiple trips to the hardware store. And don't forget a good heatsink for the uP.:smile:

---

