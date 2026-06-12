---
title: "Bluetooth the saga continues!"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by niteblind on 2006-07-12
Hi,

Still having issues with accessing bluetooth headset and headphones (1 of each). I can conect to my wifes mobile phone and send and receive files no problem so i know blue tooth itself is working but.....

the code she had to enter is 1234 which i am assuming is in the bluez-pin file. but i cannot find that file in /usr/bluez-pin so i cannot fo in and edit it. i pulled it down using apt-get and if i try a whereis command it comes back blank. anyone able to help? I think i need to change the pin as the headset work with 0000 instead.

Also my mini headphones appear in the bluetooth folder in konqueror (forgot to add i am using kbuntu) but when i click it i get an error malformed url followed by the path of the icon???? anyone got any ideas why?

cheers
niteblind

---

### Post by niteblind on 2006-07-13
errrm anybody?????
niteblind

---

### Post by wieman01 on 2006-07-13
> **niteblind said:**
> errrm anybody?????
niteblind

Have you tried the KDE Bluetooth Manager (kbluetooth)? Very useful tool that I am utilizing when connecting to my various headsets. Try it out and let me know if you have issues. I can help with the scripts once you have set it up.

My setup works fine for Skype and various sound applications. Let's see what you have done so far, then I should be able to guide you through it.

---

### Post by niteblind on 2006-07-13
I am using Kbluetooth by default as i am running kubuntu. all seems fine when connecting to mobile but when connecting to headset i get authentication failure error message. I am assuming from the fact that i HAD to enter 1234 to get the phone to connect that this is the pin the PC is trying to use which will not work with my headsets so i need to change it if that make sense or is possible

niteblind

---

### Post by wieman01 on 2006-07-13
> **niteblind said:**
> I am using Kbluetooth by default as i am running kubuntu. all seems fine when connecting to mobile but when connecting to headset i get authentication failure error message. I am assuming from the fact that i HAD to enter 1234 to get the phone to connect that this is the pin the PC is trying to use which will not work with my headsets so i need to change it if that make sense or is possible

Have you tried "0000" which is the default passkey for most headsets.

---

### Post by wieman01 on 2006-07-13
And by the way... Turning both your PC's bluetooth device and the headset off & on again helps as well. The system should ask for the PIN again after you have done so.

---

### Post by niteblind on 2006-07-13
when i connect the bluetooth headset i do not get a prompt to enter a pin as i do when i connect the mobile. this is why i believe that there is a pin set in the bluez-pin file that is set to 1234. Now the wierd thing is although my pin_helper is set to /usr/bluez-pin there is no file there.

As a result i do not know where to change the pin number the pc is using.

niteblind

---

### Post by niteblind on 2006-07-13
okay can i get a straight answer to this one question....

is there a file in the OS that contains a PIN that the system uses when authenticating bluetooth if so where is it.

niteblind

---

### Post by wieman01 on 2006-07-13
> **niteblind said:**
> okay can i get a straight answer to this one question....

is there a file in the OS that contains a PIN that the system uses when authenticating bluetooth if so where is it.

Straight answer: Yes, there is.

/etc/bluetooth/pin

Have you installed "btsco"? If yes, try to connect to your headset using these commands:

hciconfig hci0 voice 0x0060
btsco -v 00:00:00:00:00:00 [MAC address of your headset]

Now your computer should be asking for your pin.

---

