---
title: "create iPhone custom ringtones from MP3 to M4R on iOS 4.0.2 3GS with Ubuntu 10.04"
date: 2010-09-08
forum: Apple Hardware Users
---

### Post by tommawat on 2010-09-08
Here is a how I create custom ringtones on iPhone iOS 4.0.2 on 3GS (I am not sure about other iOS and phones).

Overview:
1. get any mp3 and open it with a programme called 'sound converter' from the Ubuntu software center and convert from mp3 to m4a format.

2. rename the file to .m4r so the iPhone recognises the file as a ringtone later

3. put the .m4r file into the iPhone by copying it from your computer and pasting it into /iTunes_Control/Ringtones folder on your iPhone 

4. open the ringtones playlist in the iPhone which can be found at: /iTunes_Control/iTunes/Ringtones.plist . You can open the playlist file by double clicking it.  Once open, there will appear a list of your ringtones.  Each ringtone has an entry such as this one from my phone:


1.  <key>ringtone file name here.m4r</key>
2.  <dict>
3.  <key>GUID</key><string>1A522500902B7003</string>
4.  <key>Name</key><string>Ringtone name here</string>
5.  <key>Artist</key><string>Artist name here</string>
6.  <key>Total Time</key><integer>30000</integer>
7.  <key>Purchased</key><false/>
8.  </dict>

Copy one of your entries in your list and paste it again immediately above where you copied it from.  (If you have no custom ringtone in your playlist from which to copy the text, you can always add one with iTunes and copy that forever onwards on your linux box.)

Now you will need to update following lines that you just pasted with the info for your newly copied .m4r file as follows:

In line 1. replace 'ringtone file name here' with the file name you copied into the ringtones folder earlier (I recommend you find the .m4r ringtone file and right click and go to properties and copy the actual file name to avoid mistyping)

In line 3. change the GUID by one number or letter. In my example above the GUID is the long string of letters and numbers.  I would for example change this from 1A522500902B7003 to 2A522500902B7003 (I just changed the first number '1' to a '2'; the new string cannot be the same as any other string in your Ringtones.plist file).

In line 4. change 'ringtone name here' with the name you want to see in your ringtone list on your phone

In line 5.  change 'artist name here' to the name of the artist if you wish

In line 6. change the time '30000' to the number of milliseconds of your .m4r ringtone file.  If you dont know this, you can open the .mp3 version of the file with a programme called 'Audacity'from the Ubuntu software center and find this out.  Remember milliseconds are seconds plus three extra digits, i.e. 30 seconds = 30000 milliseconds. 

Audacity also allows you to edit mp3 files (by cutting the length, fading in/out sound, or splice parts of different songs together.  If you edit that .mp3 file, you can 'export' it to .mp3, then convert it to .m4a using 'sound converter' and change the .m4a to .m4r as above.  

With this process, I found that you can override the 30 second Apple length limit of ringtones by simply entering the length of the song in milliseconds (i.e. 3 minutes = 180 seconds or 180000 milliseconds).

This has worked for me.

---

### Post by arunshankar on 2010-11-14
this is really a very good job and it almost worked for me. 

I did everything and I was also able to see the ringtone on my iPhone in sound settings option. But when i select and get back to previous screen, the ringtone is automatically set to Marimba (the default) one. Could you please let me know the reason.

Thanks.

---

### Post by J_khushal on 2011-08-14
i used this info . . . . it worked, thanks very much:KS

---

### Post by phuongdt3 on 2011-08-17
thanks so much :D

---

