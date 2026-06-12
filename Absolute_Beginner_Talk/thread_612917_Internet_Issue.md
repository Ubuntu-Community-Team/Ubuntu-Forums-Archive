---
title: "Internet Issue"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by gaganarora1 on 2007-11-14
Hi,



I'm unable to access internet, see screen shots for details. I use a ADSL broad band connection (Provider BSNL, Modem type: DLink 502T). Im able to ping the sites using the terminal however still unable to open the same from the browser, when i try to configure i get the following erroer as seen in screen shot 2. This modem is capable of storing the user ID and pwd once configured so i don't have to key it again and again!!!



Pls help!



Tx

G

---

### Post by NT4usB on 2007-11-14
Might be a DNS issue... but I wouldn't think ping would work either.

What do you have under the DNS flag?
I found using the IP address of my router in the DNS works... looks like yours is 192.168.1.1

---

### Post by badguyanil on 2007-11-14
bump! any idea why this is happening! i am cllueless..never seen anything like this

---

### Post by badguyanil on 2007-11-15
bump

---

### Post by plucky on 2007-11-15
Badguyanil,

I am no expert,but I have just been setting up a wireless modem router

Try what NT4usb said.

Click on > System > Administration > Network 

Enter sudo password
 
Click on DNS tab and add your modem router DNS which should be 

> 198.162.1.1

Then open firefox and enter in the address bar
> [http://198.162.1.1](http://198.162.1.1)

this should log you into the modem 
It should then ask you for a username and password, the default should be 
Username: ADMIN
Password: ADMIN

You can then setup your modem router
This is what worked for me,hope this helps you

Plucky

---

### Post by dineshs on 2007-11-17
I am not expert But please do the following
1.Connect only one telephone(no parellel) and that should be in the phone outlet of modem
2 Check the SNR value in the modem(I think it is in status-modem status ).It should be above 10 both up and down.If it is below 10 You need to check telephone line I think
3.your modem is already stored with user id and password,so you should make it bridged if you want to run pppoeconfig.

---

### Post by gaganarora1 on 2007-11-18
bump

The modem/router has already been configured while using Windows (in which internet is working just fine), do i need to do it again in Linux?

---

### Post by PointyWombat on 2007-11-18
if you can ping and resolve properly, then the problem is most likey your firefox.

What are your connection settings 

firefox -> edit -> preferences -> advanced -> network -> connection -> settings

direct, auto, or manual?

---

### Post by mellowd on 2007-11-18
You seem to be getting ping response from both yahoo and google. run a trace to both to see the route out to the net. Open up a terminal:

```
traceroute google.com
```

---

### Post by so7777777os on 2007-11-18
bump
I'm noob and i only can resolve some easy problem,refer to the  ping IP etc....i have no way to make it......

---

### Post by PointyWombat on 2007-11-18
What are you talking about so7777777os?? You are making no sence.

---

### Post by gaganarora1 on 2007-11-20
bump
Firefox setting:
firefox -> edit -> preferences -> advanced -> network -> connection -> settings

is set to auto as I dont use don't have to type-in my id or pwd when i wana connect to the internet.

---

### Post by PointyWombat on 2007-11-20
Change your firefox setting to 'direct connection to internet' in stead of 'auto'. It should work after that.

---

