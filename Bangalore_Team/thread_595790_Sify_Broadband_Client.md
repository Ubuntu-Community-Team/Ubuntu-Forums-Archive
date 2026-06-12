---
title: "Sify Broadband Client"
date: 2007-10-29
forum: Bangalore Team
---

### Post by vishzilla on 2007-10-29
If you have noticed, Sify have started providing version 3.0 of their linux client. I downloaded it, installed it. On using it, I get frequent disconnects with it. I want to revert back to the old client v.1.3. If anyone has the old client, plz attach it. Kindly help

---

### Post by manki on 2008-01-04
> **vishzilla said:**
> If you have noticed, Sify have started providing version 3.0 of their linux client. I downloaded it, installed it. On using it, I get frequent disconnects with it. I want to revert back to the old client v.1.3. If anyone has the old client, plz attach it. Kindly help

This is not a direct answer for your query.  Can you try MSify, available at [http://code.google.com/p/msify/](http://code.google.com/p/msify/) ?

---

### Post by gupta_sumesh63 on 2008-01-26
Yep.
I use Msify and disconnections have totally stopped.
try it. thanks to the developer.

---

### Post by manki on 2008-01-29
> **gupta_sumesh63 said:**
> Yep.
I use Msify and disconnections have totally stopped.
try it. thanks to the developer.

Thank you so much for trying out MSify and for the positive feedback.  Please let me know if I can do something to make it more useful.  (I am the developer of MSify.)

---

### Post by vishzilla on 2008-01-30
> **manki said:**
> Thank you so much for trying out MSify and for the positive feedback.  Please let me know if I can do something to make it more useful.  (I am the developer of MSify.)

how do i find the macaddress?

---

### Post by vishzilla on 2008-01-30
> **vishzilla said:**
> how do i find the macaddress?

Ok got it...never mind!!!
Its works well!
BTW, is there anyway you can encrypt the password field?

---

### Post by manki on 2008-01-31
> **vishzilla said:**
> 
BTW, is there anyway you can encrypt the password field?

If you don't want others to see your password, you can do **[FONT="Courier New"]chmod 600 .sify[/FONT]**.  This will prevent others from seeing the contents of the config file.  Given the fact that your password has to be transmitted as plaintext over Sify network, I think encrypting it locally is not worth the effort.

---

### Post by vishzilla on 2008-02-02
okk...thanks a lot..great work on it much better than what Sify provides

---

### Post by Blood_On on 2008-06-11
i followed all the steps as were stated....

now when i run the program( ~~$./msify.py ) then it gives following error....
can some one help...


[B]Traceback (most recent call last):
  File "./msify.py", line 100, in <module>
    sys.exit(main(sys.argv))
  File "./msify.py", line 93, in main
    window = MSifyWindow()
  File "./msify.py", line 18, in __init__
    self._client = sify.SifyClient()
  File "/home/savin/msify/sify.py", line 36, in __init__
    self._InitSession()
  File "/home/savin/msify/sify.py", line 42, in _InitSession
    self._sess = minidom.parse(self.sess_file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line
1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py",
line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py",
line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 2, column 0[/B]

---

### Post by manki on 2008-06-11
> **Blood_On said:**
> 
now when i run the program( ~~$./msify.py ) then it gives following error....

I don't use Sify any more, so I am not sure if Sify has changed their session file format or not.  Can you please post the contents of the file **/home/savin/msify/sify.py**?

---

### Post by grif.ghatak on 2009-02-12
try this thread
[http://ubuntuforums.org/showthread.php?p=6721614#post6721614](http://ubuntuforums.org/showthread.php?p=6721614#post6721614)

---

