---
title: "average cpu temperature"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Circus-Killer on 2007-06-13
im a bit concerned about running ubuntu on my laptop. basically, atm, when i run ubuntu on it, its starts with 51 degrees celsius, works its way up to 59 and then the fan kicks in, cools it back to 51, and the cycle begins again.

now, i want to know if this is norma. especially because my fan seems to be coming on very often at regular intervals. by often, i mean every couple of minutes. is that normal? or is my laptop being put under too much strain, risking burning out my laptop?

---

### Post by Kobalt on 2007-06-13
The temperatures you mention are regular temperatures of working on my laptop. What I do to cool it down is to use the CPU frequency applet to set it to Powersave for example.

---

### Post by Circus-Killer on 2007-06-13
hmmmm.....will have to try that frequency scaling app that you speak of tonight when i get home.
thanks for the tip. hope it helps. i'm just worried about burning out my new laptop after the first week.

---

### Post by girishv on 2007-06-13
If you are brave enough, you can also try undervolting the CPU. I got nearly 3 degree drop in temperature by this

Girish

---

### Post by Circus-Killer on 2007-06-13
nah, im definately not gonna try undervolting it. as i said, its the first week ive had this laptop. dont wanna screw it up. hence all the questions. i'm really worried about ubuntu burning out my machine. but alas, what choice do i have, im not gonna use vista. hope the frequency-scaling does help though.
thanks for the suggestion anyways, keep em coming.

---

### Post by bbarcelo on 2007-06-13
If you could post some information about your laptop such as model number or processor information, we could give you a little bit more info about the normal idling and working temperatures of your laptop. Chances are, though, if you haven't changed any BIOS settings or aren't using your computer in a 90 deg. F. room, your computer is functioning properly at those temperatures.

---

### Post by kittyhawk63 on 2007-06-13
Hope you don't mind me asking on your thread, but how does one check the temperature of a laptop? I just received a used laptop today from a friend and it seems warm to me. But I have never had a laptop before so I really don't know if it was just running normal temp.

---

### Post by Circus-Killer on 2007-06-13
well, i'm not hundred percent sure of the specs off hand, cos my laptop is at home and im at work, but here's what i remember:

HP Pavilion DV6000 Laptop
1.8GHz AMD Sempron
1024MB RAM
80GB hdd

as for changing bios settings, i havent done any changes. well, i was thinking of returning to vista, but i think i might as well take the risk and run ubuntu.

---

### Post by Circus-Killer on 2007-06-13
> **kittyhawk63 said:**
> Hope you don't mind me asking on your thread, but how does one check the temperature of a laptop? I just received a used laptop today from a friend and it seems warm to me. But I have never had a laptop before so I really don't know if it was just running normal temp.

run in terminal:
cat /proc/acpi/thermal_zone/THRM/temperature

please post back the output

---

### Post by kittyhawk63 on 2007-06-13
> **Circus-Killer said:**
> 
i was thinking of returning to vista, but i think i might as well take the risk and run ubuntu.

Not sure why you would want Vista. Have you read about all the control that Vista demands over your computer? You can't do just anything with Vista the way you could with XP. MS has tried its best to pirate your computer and take over. I would run some investigation searches over the Internet before I would go to Vista. Feisty Fawn is really a good OS. I would learn to use it and just work out your issue with the heat. Check the Internet and see what the temperature of your laptop runs at when normal.
kh

---

### Post by kittyhawk63 on 2007-06-13
> **Circus-Killer said:**
> run in terminal:
cat /proc/acpi/thermal_zone/THRM/temperature
please post back the output

I'm on my desktop PC and it would take about 10 minutes to boot up my laptop and run your command. Do you want to wait until I can get back to you? BTW, does this work on a desktop PC? I ran the command on my desktop PC and it did not recognize the command.
kh

---

### Post by Circus-Killer on 2007-06-13
to be honest, i dont want to go back to vista.

see, what happened (scuse me straying off topic), is that i bought this laptop last saturday and it came with windows vista home basic. now home basic sucks, but the cheapest upgrade to home premium costs R1800. the R stands for South African Rands (ZAR). 

that threw me right off. not a chance im paying that. besides, ive been using ubuntu on and off for a couple of years, and linux since 1999. i'm perfectly comfortable with it. my only concern is that this is a brand new laptop, and its my first laptop, so you can understand why i am cautious as to not burning out my lappy on the first week.

anyways, i figure what the hell, you only live once. might as well be a man and face the risk.

---

### Post by bbarcelo on 2007-06-13
> **Circus-Killer said:**
> well, i'm not hundred percent sure of the specs off hand, cos my laptop is at home and im at work, but here's what i remember:

HP Pavilion DV6000 Laptop
1.8GHz AMD Sempron
1024MB RAM
80GB hdd

as for changing bios settings, i havent done any changes. well, i was thinking of returning to vista, but i think i might as well take the risk and run ubuntu.

Well according to the temperatures you listed, your laptop's (the processor at least) running within acceptable temperature constraints.

Source: [Only source I could find easily]("http://www.thenerds.net/ADVANCED_MICRO_DEVICES_AMD_SEMPRON_340018GHZ_SKT_AM2_SOCKET_AM2256K_CACHE.SDA3400CWBOX.html")


> **Circus-Killer said:**
> to be honest, i dont want to go back to vista.

see, what happened (scuse me straying off topic), is that i bought this laptop last saturday and it came with windows vista home basic. now home basic sucks, but the cheapest upgrade to home premium costs R1800. the R stands for South African Rands (ZAR). 

that threw me right off. not a chance im paying that. besides, ive been using ubuntu on and off for a couple of years, and linux since 1999. i'm perfectly comfortable with it. my only concern is that this is a brand new laptop, and its my first laptop, so you can understand why i am cautious as to not burning out my lappy on the first week.

anyways, i figure what the hell, you only live once. might as well be a man and face the risk.

Vista is straight-up AWFUL. I've had numerous users complain about its "features" and had some of my friends come to me with questions about why their new $3000 machine is blue screening so much (only in Vista btw). Stay away from it. If you have to use Windows, use XP. It's not the greatest, but it is better than Vista by far. Even Dell knows that and look at what great Linux distro they support (hint: Ubuntu.).

---

### Post by kittyhawk63 on 2007-06-13
> **Circus-Killer said:**
> 
anyways, i figure what the hell, you only live once. might as well be a man and face the risk.

You could go to a lighter demanding Linux version like SAM which uses XFCE. I tried SAM and really liked it. It automatically recognized all my hardware, which none of the Ubuntu distros have and it had Beryl working out of the box. You might try a LiveCD and see what it does with your heat issue. That is, if you really have a heat issue. Maybe it is running in the normal temperature range.
kh

---

### Post by Circus-Killer on 2007-06-13
thanks so much for that link bbarcelo. you're right, everything does seem to be normal. to be honest, i specifically bought a laptop to run ubuntu on it (cos i have to run xp on desktop for hardware purposes).

anyways, i guess ill re-install ubuntu when i get home today. might also play with the frequency-scaling applet a bit to see if i can stop the fan from going on and off as much as it does. but other than that, whatever. might as well risk the laptop for ubuntu, its what i bought it for :P

---

### Post by bbarcelo on 2007-06-13
Ubuntu's a great choice. I have a laptop and a file server running it right now and am enjoying it. Your CPU fan up and down spin might be something you can adjust in the BIOS. I know the spin up can be annoying but be careful to not change your CPU's settings to a clock speed that the fan can't properly handle it (watch your idle temps.). You could always look for some Linux program that could control your CPU fan and just have it set to 80% all the time (might be loud though, but will keep your laptop cool.)

---

