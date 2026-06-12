---
title: "Bluetooth Connection Problem"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2007-07-26
Hello, I'm a Ubuntu newbie and I just found my old Belkin F8T003 Bluetooth USB adapter. I want to be able to transfer files between my phone (Sharp GX-17) and my computer.

I installed "Bluetooth FIle Sharing 0.8.0" and my phone can now detect the computer. When I try to send a file to my PC it asks if I want to pair the devices, I press "ok" and it asks for my passcode. Following [this]("http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu") tutorial I managed to change the passcode to "0000" from "1234". When I enter in the passcode though I get an error saying "Connection is Disconnected. Try again?" If I try again it  just repeats, and if I cancel nothing happens.

Since I have used my phone to transfer files without problem, and the adapter seems to be working fine I am guess it is a problem with Ubuntu or the software. Does anyone else have any other ideas or ways to try fix it?

Thanks.:)

---

### Post by doomster on 2007-07-26
i tried to solve this problem several days ago.. it seems to be a Feisty  problem on pairing 2 bluetooth devices, and i didnt get to any solutions :( in edgy this worked without problems.. all we have to do is try harder, and wait for an update:)

---

### Post by ddrichardson on 2007-07-26
I don't know if this will help - but I had problems pairing too and got it working by using bluez-tools and sending files by right clicking in evolution and sending.

To recieve I ran Applications/Accessories/Bluetooth File Sharing and then deleting the history and my phone and was able to pair.

---

