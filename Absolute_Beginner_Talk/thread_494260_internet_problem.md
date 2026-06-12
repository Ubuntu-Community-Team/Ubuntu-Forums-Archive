---
title: "internet problem"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by jimbean on 2007-07-06
everytime i pull the power to an asus motherboard with a nvidia chipset {and the put power to it again}

i will loose my internet

my soulution is to plug my backup computer an {via chipset}

and it resets my asdl modem so i can use the internet on my new computer {nvidia chipset}

is there a setting that i need to enable {ifconfig or network setting} ,and or do i need to install the nvidia chipset drivers

this is a wired connection

with 1 computer at a time hooked up

ubuntu fiesty

---

### Post by shrift on 2007-07-06
I'm sorry... You're a bit unclear about the actual problem. Of course when you take power away from your computer the internet does not work anymore. 

Can you be a little clearer about what is going wrong? Like, why is the power going out? Are you physically pulling the cable?

---

### Post by jimbean on 2007-07-06
i manually unplug for my own reasons 
it happens when i unplug the modems power or the computers power

---

### Post by shrift on 2007-07-09
Ok, well it sounds to me like the issue is with the modem not Ubuntu. I have weird issues getting my cable modem to work again after I unplug it as well. The key is to either power cycle it and plug it back into the same computer whie it's booting, then tell your computer to look for an IP, (sudo dhclient eth0) or you can plug it into a different computer like you were doing and that makes the modem send a new IP out. They tend to get confused.

---

### Post by jimbean on 2007-07-12
as of right now i figured out that if i type (sudo pon dsl~provider) it pings or wakes up modem

I have to let it run about 40 lines of giberish in the terminal then i can connect to internet

sometimes i have to reboot but i have internet one way or the other

thanks for the help

i believe its the modem also

---

