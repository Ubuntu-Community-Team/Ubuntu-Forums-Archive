---
title: "PDA can sync in a test-user account but not in my main user account"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-06-28
Hello,


I have a funny situation. I created a new user account just to test things out. On that test-user account, I'm able to sync my PDA by doing the following: 

1) Enter "sudo modprobe visor" in terminal.
2) Press Sync on Sony PDA.
3) Press Sync on Jpilot.

I then hear the twaddle dee sound.
 Here is what  "$ tail -f /var/log/messages" gives. 


[SIZE=3]On Test Account[/SIZE]


Before anything else:
Jun 28 17:12:04 jc-amd kernel: [ 2006.112000] [fglrx] free       Inv  = 134217728
Jun 28 17:12:04 jc-amd kernel: [ 2006.112000] [fglrx] max single Inv  = 134217728
Jun 28 17:12:04 jc-amd kernel: [  2006.112000] [fglrx] total      TIM  = 0
Jun 28 17:12:15 jc-amd gconfd (clie6-7095): starting (version [2.18.0.1]("http://2.18.0.1/")), pid 7095 user 'clie6' 
Jun 28 17:12:15 jc-amd gconfd (clie6-7095): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
Jun 28 17:12:15 jc-amd gconfd (clie6-7095): Resolved address "xml:readwrite:/home/clie6/.gconf" to a writable configuration source at position 1
Jun 28 17:12:15 jc-amd gconfd (clie6-7095): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
Jun 28 17:12:15 jc-amd gconfd (clie6-7095): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 28 17:12:15 jc-amd gconfd (clie6-7095): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
Jun 28 17:12:16 jc-amd gconfd (clie6-7095): Resolved address "xml:readwrite:/home/clie6/.gconf" to a writable configuration source at position 0

After pressing Sync on Sony PDA:
Jun 28 17:15:18 jc-amd kernel: [  2200.684000] usb 1-4: new full speed USB device using ohci_hcd and address 17
Jun 28 17:15:18 jc-amd kernel: [ 2200.892000] usb 1-4: configuration #1 chosen from 1 choice
Jun 28 17:15:18 jc-amd kernel: [ 2200.896000  ] visor 1-4:1.0: Handspring Visor / Palm OS converter detected
Jun 28 17:15:18 jc-amd kernel: [ 2200.896000] usb 1-4: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jun 28 17:15:18 jc-amd kernel: [ 2200.896000  ] usb 1-4: Handspring Visor / Palm OS converter now attached to ttyUSB1


After pressing sync on jpilot:
Jun 28 17:15:30 jc-amd kernel: [ 2212.764000] usb 1-4: USB disconnect, address 17
Jun 28 17:15:30 jc-amd kernel: [  2212.764000] visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
Jun 28 17:15:30 jc-amd kernel: [ 2212.764000] visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1 
Jun 28 17:15:30 jc-amd kernel: [ 2212.764000] visor 1-4:1.0: device disconnected



-------------------------------------------------------------------------------
[SIZE=3]On my main account[/SIZE]

jc@jc-amd:~$ tail -f /var/log/messages 
Jun 28 17:19:57 jc-amd gconfd (jeff-5085): starting (version [2.18.0.1]("http://2.18.0.1/")), pid 5085 user 'jc'
Jun 28 17:19:57 jc-amd gconfd (jeff-5085): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
Jun 28 17:19:57 jc-amd gconfd (jeff-5085): Resolved address "xml:readwrite:/home/jeff/.gconf" to a writable configuration source at position 1
Jun 28 17:19:57 jc-amd gconfd (jeff-5085): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
Jun 28 17:19:57 jc-amd gconfd (jeff-5085): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 28 17:19:57 jc-amd gconfd (jeff-5085): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
Jun 28 17:20:02 jc-amd gconfd (jeff-5085): Resolved address "xml:readwrite:/home/jeff/.gconf" to a writable configuration source at position 0
Jun 28 17:20:17 jc-amd kernel: [  139.064000] usb 1-4: new full speed USB device using ohci_hcd and address 2 
Jun 28 17:20:18 jc-amd kernel: [  139.276000] usb 1-4: configuration #1 chosen from 1 choice
Jun 28 17:21:18 jc-amd kernel: [  199.744000] usb 1-4: USB disconnect, address 2



After I press the sync button on the PDA: 
Jun 28 17:26:01 jc-amd kernel: [  482.384000] usb 1-4: new full speed USB device using ohci_hcd and address 3
Jun 28 17:26:01 jc-amd kernel: [  482.592000] usb 1-4: configuration #1 chosen from 1 choice
Jun 28 17:26:01 jc-amd kernel: [   482.596000] visor 1-4:1.0: Handspring Visor / Palm OS converter detected
Jun 28 17:26:01 jc-amd kernel: [  482.596000] usb 1-4: Handspring Visor / Palm OS converter now attached to ttyUSB0
Jun 28 17:26:01 jc-amd kernel: [   482.596000] usb 1-4: Handspring Visor / Palm OS converter now attached to ttyUSB1



When I press the sync button on Jpilot:
Nothing happens!





How come in my main account, though PDA is connecting to my computer, Jpilot does not seem to connect with the computer/PDA? I've tried changing Jpilot/File/Preferences/Settings Tab/Serial Port from the default of [usb:] to [ttyUSB1] and  [ttyUSB1:] but it just makes things worse.(doesn't help). 


Please help me.

---

