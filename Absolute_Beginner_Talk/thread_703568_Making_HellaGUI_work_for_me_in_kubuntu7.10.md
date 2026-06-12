---
title: "Making HellaGUI work for me in kubuntu7.10"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by max renn on 2008-02-21
[SIZE="1"]I'm new at this, I don't know the ins and outs of Python, etc.  If someone wants to suggest something better, easier, please do :)[/SIZE]

**Making HellaGUI work for me in kubuntu7.10**

So I loaded hellanzb and it works.  I wanted a gui, of course.  There are three available (other than web-based), and I chose hellagui since it uses python 'just like hellanzb'.

The meager install offerings provided by the developer suggest I untar and start the gui by clicking on icon or run command '/.hellagui'.  Nice, but at least there was that much.  Unfortunately, there is no '/.hellagui' after untar.  Hmmmm.  There is a hellagui1.1.1 dir.  There is a hellagui1.1.0 file identified as a python file in that dir.  So I click it and it opens in kate or something.  grrrr.:confused:

Hmmm, I can run hellanzb at the terminal line and it works, but 'hellagui1.1.0' doesn't.  Of Course.  I remember running hellanzb in windows as 'python hellanzb' so I try ```
'python hellagui1.1.0'
``` and it works!  But it has an error.  ```
'hellanzb is running but there seems to be a problem'....
```  Nothing new, my whole life is one big problem...

Ummm, yeaah.  OK, I have no clue, so I look around a little and finally notice there is now a dir '/.hellagui' in my home dir.  FM!  I look in there and see a hellagui.conf file and in that there is a line```
 self.hellaPW=""
```.  I remembered seeing a similar line in the hellanzb.conf,```
 Hellanzb.XMLRPC_PASSWORD = 'changeme'
``` (the only reason that looked similar is because I accidently read somewhere that hellanzb uses a password when an external program accesses it), so I took the logical route and changed them both to the same password.

So I kill all hell* processes and run ```
'python hellagui1.1.0'
``` again in terminal and it works! but tells me thet hellanzb is not running, so I restart hellanzb in hellagui and now it is all running and with the added bonus of no extra terminal window open!  Getting somewhere!

Well, I don't like this terminal start, and I haven't figured out runlevels yet, so I create a shortcut in the K Menu that allows me to open the GUI like any other app.

```
1. Right click K-Menu Icon at lower left of screen
2. Select Menu Editor
3. Right click on Internet
4. Select New Item
5. Enter Item Name (HellaNZBGUI) and click ok
6. Enter Description (HellaNZB Gui)
7. Enter Command ('/home/myalias/hellagui1.1.1/hellagui1.1.0')
    *note:  I originally entered ('/home/myalias/hellagui1.1.1/python hellagui1.1.0'), but that seems to have auto changed, but still works, weird*
8. Enter Work Path (/home/myalias/hellagui1.1.1)
9. Close Menu Editor
10. Choose "Save" changes
```

Now I have only a gui to worry about.  I changed my settings in hellanzb.conf so my .nzb gets automatically processed when I download them to my downloads dir.  Unfortunately hellagui only has a pause, not a stop function, so I have to still kill the process if needed, but otherwise a fine gui.:popcorn:

---

