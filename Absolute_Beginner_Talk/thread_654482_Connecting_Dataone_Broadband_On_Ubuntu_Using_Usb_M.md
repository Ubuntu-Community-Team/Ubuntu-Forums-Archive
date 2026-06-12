---
title: "Connecting Dataone Broadband On Ubuntu Using Usb Modem"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by SOUMYA86 on 2007-12-31
I Have A Huawei Quidway Wa 1003a Modem.....
Its Lan Point Is Not Working...so
I Connect To The Net Using The Usb Port...in Windows...
How Do I Get It Working In Ubuntu(its 64bit)....
This Is My First Time In Liunx......

---

### Post by K.Mandla on 2007-12-31
Moved to Absolute Beginner Talk. :)

---

### Post by mridkash on 2007-12-31
I tried doing this but couldn't. I have huawei mt 841 modem, its driver cd had linux drivers too but couldn't figure out how to install them.

Does your modem driver CD has linux drivers? If yes, post the contents of the folder here so that people can see how to install it.

---

### Post by ashmew2 on 2007-12-31
I dont know if this will work but i tried using USB to access my Airtel Broadband , with router Beetel 220BX , I just put in the USB and internet was running. Plug n' play sort of. U might wanna try.

---

### Post by SOUMYA86 on 2007-12-31
thats the problem....
that cd does not have 
any linux drivers.....

---

### Post by sreekanth.mk on 2007-12-31
> **SOUMYA86 said:**
> I Have A Huawei Quidway Wa 1003a Modem.....
Its Lan Point Is Not Working...so
I Connect To The Net Using The Usb Port...in Windows...
How Do I Get It Working In Ubuntu(its 64bit)....
This Is My First Time In Liunx......

I will help you tru the following
Ethernet Connection

   1. Connect the modem/router to the ethernet card
   2. Assign an IP address for the ethernet card; the router has a fixed interface address of 192.168.1.1, so you can use 192.168.1.2 for your ethernet interface.

      $ sudo ifconfig eth0 192.168.1.2

   3. Add 192.168.1.1 as default gateway.

      $ sudo route add default gw 192.168.1.1

   4. Enter the address of some DNS servers in /etc/resolv.conf. These DNS adresses are provided on BSNL's instruction manual.

      $ sudo vi /etc/resolv.conf


      The entry will be of type nameserver 61.1.96.71, where the IP will be the one provided in your BSNL Broadband instruction manual.
   5. Access the router's management interface via a browser by typing the address 192.168.1.1. The admin username/password is admin/admin 

    * Set the connection type to `PPPoE'. On my MT882 box, this comes under `WAN Settings'
    * Enter your user name and password (username is of the form xyz@dataone)
    * Reset the router. It will take 2-3 minutes for the box to come up again 

Steps 2, 3, 4 can also be done from menu System->Administration->Network in GUI

Alternate Method:

   1. Connect your ethernet wire to the port at the back of your computer.
   2. Fire up the terminal and type in sudo pppoeconf
   3. It should detect your modem.
   4. Keep on pressing enter. Fill in your user name and password when indicated.
   5. It should be easy to stick on to defaults.
   6. You should be prompted back to your terminal when it would say pppoe loaded. Simple. That's the end of terminal. 

Now go to System>Administration>Networking. Click on it. You would be asked for your password to carry out the administrative job as root. You should be prompted to enter the following details.

   1. Activate the Wired connection.
   2. Highlight the wired connection and click on properties.
   3. Check the box "enable the connection"
   4. Configuration as Static IP.
   5. IP Address : 192.168.1.2
   6. Subnet mask fills on it's own as 255.255.255.0
   7. Gateway address :192.168.1.1 
**IP ADDRESS AND OTHERS ARE INCLUDES IN YOUR DATAONE USER MANUAL**

---

