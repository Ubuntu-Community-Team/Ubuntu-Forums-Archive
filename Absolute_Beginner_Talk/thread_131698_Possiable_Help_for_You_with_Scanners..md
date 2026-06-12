---
title: "Possiable Help for You with Scanners."
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by LateNighter on 2006-02-16
I am not New to Linux but am Far from an Expert.
  So I can't say this will HELP everyone if they are trying to run Kooka on their Scanner. 
  
  I had not had this problem until I upgraded to Brezzy, all the Usual Stuff did'nt work to get Kooka running on my Scanner, So this is what I did.

  AND GUESS WHAT IT ACTUALLY WORKED!!!\\:D/ 
  
 I had installed Kooka and Sane just as I had a Million Times.

 But Kooka kept detecting my Microtek 3600 Scanner, but when I would Hit the do you want to use this Scanner, and went into the Startup Screen,  In the lower Left Corner it told me...:rolleyes: 

 Scanner Not Found, You do not have SANE Installed or Properly install.
 
 I knew it was installed but somehow Not Linking up right so this is what I did.
 I figure it should Work as well with Other Scanners as well as Microtek's.

 It's worth a shot, THIS IS WHAT I DID:

 #1. First off Extract SANE Backend .tar files to the following Directory.
 usr/lib/sane   Close out file after this is Completed.
    You'll have to Make a Folder to extract the SANE backends to.
    Then Move to Trash Can the files already in usr/lib/sane directory.
    Move the extracted SANE backend files to usr/lib/sane.
    Then Restore the files removed from the Trash Can back to usr/lib/sane.

 #2. In Synaptic Make Sure the following files are installed.
        gcc Compiler.
        libusb.
        libjpeg.
        libeee1284 (This is only needed if your Scanner runs off a Parallel Port)
        libgphoto2.
 
        Also make sure to install all Gcc Compiler Files, That are the NEWER Ones, 
        As Well as all of the SANE pkgs that are Upto Date.
   
 #3. Go To: K Launch/Graphics/Kooka= Right Click/Edit Item.
        Now Change the Command Line to the following using the Browse File Feature.

        '/usr/bin/kooka'

       Next Enable/Check Launch Feedback.

       Then Enable/Check (Run as Different User)

       Username: root

       X out of Screen (Then Click on Save Sys Config)

       Then hit the Kooka Icon, Login using your User Password and there you have it.

     You should now have a Working Scanner.   \\:D/ :-k \\:D/

---

