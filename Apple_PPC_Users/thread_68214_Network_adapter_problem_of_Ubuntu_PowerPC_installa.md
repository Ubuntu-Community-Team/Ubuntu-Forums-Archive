---
title: "Network adapter problem of Ubuntu PowerPC installation on iBook G4"
date: 2005-09-22
forum: Apple PPC Users
---

### Post by gaobo on 2005-09-22
I am a green hand in Linux usage. But I think I have experiences in the field of computer for many years. So if anyone has technical ideas please feel free to express it. Thanks first way.

The Ubuntu Linux cannot recognize my network adapter on the iBook G4. I am not meaning the AirPort Wireless, but the Wired one. I wanted to download the driver for it but cannot find it anywhere via Internet. Nobody can answer me even which model of ethernet network adapter is iBook G4 using.

So now I cannot use Ubutu PowerPC on my iBook G4 to connect to Internet, which is making me not so happy.

Any idea on this will be highly appreciated. How I want to get connected to Internet in Ubuntu PowerPC installation on my iBook G4!

---

### Post by callipeo on 2005-09-22
[QUOTE=gaobo]The Ubuntu Linux cannot recognize my network adapter on the iBook G4. I am not meaning the AirPort Wireless, but the Wired one[/QUOTE]

Do you mean you cannot use the ethernet port?

---

### Post by gaobo on 2005-09-22
You are correct. What I want to use is just ethernet port but not AirPort. I seldom use wireless connection to be honest. But not being able to use wired connection makes me very sad.

---

### Post by Arne Caspari on 2005-09-23
The ethernet adapter should be detected fine with the iBook G4. Are you sure the adapter is not detected? Maybe you just need to configure an IP address? 

After booting upuntu, there should be a network applet in the top panel of the Desktop. Right click it and select "properties". In the dialog, that comes up, enter "eth0" in the "name" field to see if you can configure it.

---

### Post by callipeo on 2005-09-23
If the procedure mentioned in reply #4 does not work (which would be really strange in my opinion), you could check if the driver is loaded with "lsmod | grep sungem". You should see two modules loaded.

---

### Post by gaobo on 2005-09-23
[QUOTE=callipeo]If the procedure mentioned in reply #4 does not work (which would be really strange in my opinion), you could check if the driver is loaded with "lsmod | grep sungem". You should see two modules loaded.[/QUOTE]

Arne and you are both correct, now I am sending this post under my iBook G4 happily.

Ubuntu is really a great operating system that is reachable at present. :-)

Daniel

---

