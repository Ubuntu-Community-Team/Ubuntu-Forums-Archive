---
title: "Problem with wireless networking"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Matiesz on 2007-06-21
I've decide to givee Ubuntu a try, so I download the ISO burn it to a CD and boot. Everything runs fine, the OS finds my wireless card and even the network I'm normally using under windows XP. Only while in Ubuntu I cannot connect to it. Maybe it's because I've not install it yet or whatever. I know nothing about Linux and I don't know what to do. My computer has a Linksys wireless-G PCI card and the router is a Lynksis wireless-G broadband 2.4 Ghz router model WRT54GS. Is there any way I can have internet under Ubuntu?

---

### Post by PartisanEntity on 2007-06-21
Do you use any kind of encryption on your router?

Also, assuming you are using the latest version of Ubuntu (7.04 aka Feisty Fawn) then if you look at the top panel, on the right you should see network manager, the icon looks like two small computers, if you click on it with the left mouse button does it show you any wifi networks in your area?

---

### Post by Matiesz on 2007-06-21
Yes the networks available are shown I can try to connect to them but it just won't work. I've the most recent version, 7.04 that is. And for the encryption part AFAIK I don't but a friend of mine installed the router so I wouldn't know for sure.

---

### Post by PartisanEntity on 2007-06-21
How did you connect in windows? Did you have to enter any passwords?

---

### Post by Matiesz on 2007-06-21
In windows I can connect without problem and without a password, in fact I'm under XP to see this forum right now.

---

### Post by Spooky5 on 2007-06-21
I also have a linksis Wireless G card and router. I don't have the model numbers off hand because I am at work. My card detects the network but will not connect to it. My network connection is WPA encrypted, which I've tried connecting to with WSID but it locks up the computer. I've tried switching over to WEP and it still will not connect.

---

### Post by bobosky on 2007-06-22
Well it looks like I am in the same boat. I installed the latest Version of Ubuntu last night and now I am trying to get the computer to even find and wireless connection. I have a Linksys Wireless G WPC54GX4 if that helps and a mac Airport. Where my problem differs from the rest is in Network Settings I only get Wired connection and Modem connection as options. The computer does not evern see the wireless connections. 
My Airport is WPA encrypted. 
What other info should I give to help find the answer to this problem?

bobosky:popcorn:

---

### Post by gigaferz on 2007-06-23
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#dns)

try this

also read this 
[http://ubuntuforums.org/showthread.php?t=172810&highlight=wep+wireless](http://ubuntuforums.org/showthread.php?t=172810&highlight=wep+wireless)

   Now let me tell you something:

       I bought my zonet adapters,  i went trhough a lot in one machine, I ended up compiling ndiswrapper and modprobing, etc...

   When it was time to get on the other machine,,I just updated ndiswrapper and after provifding the driver, it just worked.

   I realize I had some unknown guest on my wireless area, so I decided to put a password on it.
   I wetn to the http of my router and put WEP protection.
   
  It took me 1 weekend to figure it out.I just couldnt connect to my own "network"

   By the way none of the gui apps i use were working- wifi radar or network manager.

   I went to the comand line    and it worked (please read the documentation then the post )

   But in order to get connected right away I  had to edit the interfaces config file.

like this:

auto wlan0
iface wlan0 inet dhcp
wireless-essid ferby
wireless-key open s:mombo

im using ASCII for the password there is also hexadecimal, , open,shared,restricted,???

I hope this can help you out somehow...remember start from the begining.

---

