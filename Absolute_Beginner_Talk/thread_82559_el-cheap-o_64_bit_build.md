---
title: "el-cheap-o 64 bit build"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by grimmson on 2005-10-26
Hello all. Just wanted a consensis on an el-cheap-o 64 bit build. Getting very close to the purchase. I've read very little about 64 bit linux and wnat to know if you think I'll have any problems.

ECS K8M800-M2 
Gforce FX5200 128
FPS 300 watt ps FSP300-60GLS 
2800 Sempron 754 pin 256 L2
Corsair VS256MB400  256 ddr 400 cl 2.5
Nec dvd burner ND-3540A 

I know this isn't cutting edge but I want a low end 64 bit system. All this for $300. I'll scavange a 40 gig maxtor in my house. 
     Tidbits of info. The power supply is only 300 watt. I've selected it because its close to all I'll need and it only draws 4 amps 120vac. Thats the lowest ac power supply I've ever seen. I'll need 237 watts at %100 according to [http://extreme.outervision.com/index.jsp](http://extreme.outervision.com/index.jsp)
     The k8m800 has a "S3 Graphics UniChrome Pro IGP". This system will mostly be a high powered dvd player. I could drop the $30 gforce and double the corsair for $12 (256 = $28, 512 = $40) and still be under $300. I don't think I need much gpu power so should I share 512 or use 256 w a fx5200?
     This is kinda funny. I started out with an AST 486-66 for $1600. Ten years later I'm building a $300 2800 mhz (budget) pc and I'm picking it apart. Will it ever be fast and cheap enough? Amd and Intel hope not. Thanks for your thoughts (and warnings).

---

### Post by John.Michael.Kane on 2005-10-26
I dont think there will be any issues. also if you want have a look around ebay you may get a deal on a 64bit laptop or other parts..

---

### Post by grimmson on 2005-10-26
Thanks. I've heard xp 64 can be buggy (especially drivers.) How is Ubuntu 64?

---

### Post by Dr. Nick on 2005-10-27
I have a very similar setup as you

I have the ecs k8m800-m2 but it doesnt have integrated video
350wt Antec Smart Power power supply
and a 3000 amd64

Where are you purchasng from? My ecs didnt have integrated video card but I got a bundle deal on it and the chip for $150 U.S. I believe, several months ago. It was somewhere in that area but the chip was oem so I had to buy a heatsink.

The ecs seems well supported in ubuntu 64, worked for me out of the box.
Ubuntu 64 in general is good except lack of flash player (macromedias fault)
Drivers seem good unless you need ndiswrapper if you put a wireless card in it. Their is some problems their as the win drivers are 32bit and ndis wrapper 64 bit doesnt like that.

I have a older s3 in my laptop and its ok, not sure how good the newer ones are and how hard it is to get 3d accelration.

If you are just playing dvds and dont need 3d acell. I would drop the videocard and use itegrated if it works well.

---

### Post by nitricacid on 2005-10-27
If you really want a CHEAP-0 build (desktop) then you might want to check out getting an XBOX.

List of parts.
XBOX - $150 (less is used)
MODchip - $50-$75
Ed's Bootdisk - $??? (prolly cheap)
Xbox cord to USB - $10
A Flavor of Linux - Free

If you are really good at building, and soldering then you could make your own USB cords so you can use keyboards and mouse on the xBox.

And all of this can be hooked up to your Tele so you would be able to have a home theatre if you wanted, not to mention some killer tunes for parties.

---

### Post by grimmson on 2005-10-27
There are two versions of this board. 1.0 & 2.0 according to ECS. One with video and one without seems like a strech. My system is listed here [http://www.newegg.com/Product/Product.asp?Item=N82E16813135170](http://www.newegg.com/Product/Product.asp?Item=N82E16813135170) You may have an OEM (dell,compaq) specific board and they wanted some video card bragging rights so ordered w/o the integrated vid. Glad to hear 64 bit seems good. I'm too new to linux to deal with real problems. This is a 754 pin board  and the cpu has 64 bit extensions. Thats a bit past me. It sounds like The 754's are sudo 64 bit while 939's are true 64? That means I'll need ubuntu 64 or in a 754 pin world is ubuntu 32 better?
As for the Xbox I have two one with xecuter. Love it. Havent gotten around to dual booting. My five year old likes to make $50 frisbiees so a chip was deffinately in order. Speaking of the box, can we use faster dvd's yet or do you still have to use xbox specific for games?:cool:  The mod box has a dvd problem and I'd like to go to 16x?

---

### Post by Dr. Nick on 2005-10-27
Hmm gues newegg doesnt have my board, not sure what version number it is, I think 1 by looking at the ecs site. Its not oem as it came in the origional ecs retail box when I bought it from Frys Electronics.

Thier are no real big problems, Most of the popular applications are ported but if you want to use a lesser known application you may have to compile it from source.

The 754s are the "budget" 64bit chips. Their are a few differences between them and the 939s. The 754 will not run dual channel memory, 939s will.
Also they have different cores and manufacturing processes. Most if not all 754 are based on the same manufacturing technology as the Athlon XP while the 939 is a newer process which helps the 939 to run cooler than the 939s

The 64 bit Ubuntu will be fine as long as you have a 64bit chip, Their is no applications that require the 939 socket over the 754.

If you have a Frys electronics in your area you may check their combo deals. Sometimes a combo is a better value , but when its not a combo its usually better to go newegg or other online store. I love newegg and have bought alot from them ,but when I saw that combo at frys it was less than $10 more expensive than just the processor at newegg so basically I bought the chip and got a free motherboard.

I think the 64bit Ubuntu is mature enough for everyday use, I use it daily. But if you have any problems the 32bit will run on it as well, so you may just try both out and see what works best

---

