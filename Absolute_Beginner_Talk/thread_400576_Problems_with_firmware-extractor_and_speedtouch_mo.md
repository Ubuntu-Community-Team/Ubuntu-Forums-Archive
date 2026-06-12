---
title: "Problems with firmware-extractor and speedtouch modem"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by nodcero on 2007-04-03
Hi Everybody,

I'm completely new to the Linux game, and so far I am mightily impressed, but now I seem to have reached the limit of what I'm able to do without help.

After days of searching high and low this:

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

seems to have been the answer to getting my Thompson speedtouch UBS ADSL modem not only recognised but also working, but I am perfectly unable to get the firmware-extractor to do it's job.

Following the online instructions I got stuck at the 

unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012

part, as ./firmware-extractor seems not to be an executable file, and trying to follow my way through the README file of the extractor I also end up with neither speedtch-1.bin nor speedtch-2.bin after ./configure, which just about manages to identify the right /bin/firmware directory, but a subsequent make command brings nothing but a lot of various error messages, all indicating that it does also find bugger all to work with.

Can't be as simple as that I shouldn't try to do all the magic on my desktop?
Could the .zip file be corrupt and if so, any idea of a link to another one?
Or is there after all an easier way to get the modem working?

---

### Post by Valstorm2323 on 2007-04-04
I think I know where you went wrong cause I did the same thing.



Go back to the site where you found the symbol page and download that page/save it as file.
(Yep, the page with all the symbol coding on it is the one you want!!)

Burn it onto a CD or floppy, boot up ubuntu. Transfer the file to the speedtouch folder and then use the commands you got from web in the terminal.

From there just do what the instruction told you.

---

### Post by nodcero on 2007-04-05
Thank you for the tip, I tried to follow it to the letter, and again:

unzip SpeedTouch330_firmware_3012.zip &&
chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012

evokes as response 'bash: ./firmware-extractor: is a directory'

Still no clue where I'm going wrong...

---

### Post by Valstorm2323 on 2007-04-06
Did you go here [http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor](http://www.linux-usb.org/SpeedTouch/firmware/firmware-extractor)
That's the page with all the coding on it.
Save it as it wants to be saved.

Copy it to a floppy or a cd.

Boot up ubuntu.

Put that file into your speedtouch FOLDER by dragging and dropping it is the simplest way.

Check that your speedtouch folder has that file as well as the ZZZL_3.012 file.

Go to your terminal and enter this command>   cd speedtouch

Then enter this command> dir

If your files don't show up in the terminal window then you did something wrong.

Okay if that works then apply this command>  chmod +x firmware-extractor

Then apply this command> ./firmware-extractor ZZZL_3.012
This will extract two BIN files from ZZZL_3.012 and leave them on your speedtouch folder.

I think you are still not getting the right file from the web, hence you keep getting told the error you mention.

Let me know step by step as to what you are doing so I can spot where you are making that mistake.

---

### Post by Valstorm2323 on 2007-04-06
By the way once you've done everything EXACTLY as you read it then you may need to do this once you are in ubuntu>

go to terminal
do this command>    sudo pppd call speedtch
It will prompt for password so enter your ubuntu password 

You should now be connected. Try the browser.


To make sure the ADSL is actually UP and running do this command>
tail -f /var/log/messages

Somewhere in there you should see it mention> ADSL is UP.

If it is then all you have left is to properly configure the script file.

---

### Post by nodcero on 2007-04-08
Yup, it _had_ been the wrong download of a whole firmware-extractor folder, which threw me completely off track. With the single executable file of the last link it worked like a charm.

Thank you very much.

---

### Post by Valstorm2323 on 2007-04-09
No problem.

Just happy you got your internet working!

---

