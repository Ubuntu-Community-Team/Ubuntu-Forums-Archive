---
title: "runaway app"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by garry4o on 2006-10-26
I have a runaway application I would like to terminate properly. I have openoffice-calc attempting to load an Excel8 spreadsheet(Office 97). The .xls has a single vba function, which calc sees as a macro. It is unable to successfully execute the function and produces an error. There are approximately 1000+ cells which call the function, and I'm tired of clicking OK to proceed to the next cell, and I felt it is time to learn to kill an application. The .xls works fine under Excel8, Windows. None of the documentation I have found tells me how to kill an application. I'm sure there must be some way. Any help will be appreciated - both in how to kill the app, and where to find this info in the documentation.

Thanks in advance:confused:

---

### Post by davmac on 2006-10-27
Not sure it is the right way but this is how I do it. First I find out exactly what the application is called by opening up a terminal window and typing "ps -e | grep sometext" where sometext is part of the name I'm looking for. In this case try "ps -e | grep office" and you'll see two running processes soffice and soffice.bin.

Then you can use "killall soffice" and "killall soffice.bin" to terminate the applications.

Hope this helps,

Dave Mac

---

### Post by garry4o on 2006-10-27
Thanks, this sounds reasonable, but I wonder if there might be some specific order to kill that, if improperly done, creates even more problems. I ended up pressing enter 1400 times (the actual number of cells in the worksheet containing the function). Then the sheet came up, and I was able to see the function. It contained a reference to an Excel function (there was no vb function to perform what I needed, so I called back to Excel). That long object string really confused the basic in openoffice.calc. I am converting slowly from Windows to Linux, and much of Office is what I normally do, so this was a test of sorts. Looks like much learning is in the works, but Microsoft's recent moves (WGA for XP, and who knows what else in Vista) is moving me away, if I can do 99 % of what I need, goodby Windows. At least I do have time to make the switch.

Thanks again

BTW , is there a source showing the terminal commands. I'm not afraid of reading and trying. I did a search on "kill an Application", but nothing of use showed up.

---

### Post by davmac on 2006-10-27
I suppose if you're killing apps willy-nilly there's always the potential to upset the stability of the machine, but it's probably better than having to click "ok" 1400 times!

One of the most useful resources I've found for the different commands available is [http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

I'd also recommend, when searching for answers, try Google's Linux search at [http://www.google.com/linux](http://www.google.com/linux). If you search for "kill application" you get several likely looking links to solutions.

Hope this helps,

Dave Mac

---

### Post by compmodder26 on 2006-10-27
If using Gnome: go to System->Administration->System Monitor.  Select the Processes tab and then find the process in the list and click "End Process".

---

