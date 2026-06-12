---
title: "question about the adesklets"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by thungmail on 2008-03-18
i get a message after try to execute adesklet
[PHP]
tuan@tuan:~/Desktop/weatherforecast-0.2.0$ ./weatherforecast.py
Do you want to (r)egister this desklet or to (t)est it? r
Traceback (most recent call last):
  File "./weatherforecast.py", line 40, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets interpreter initialization error - Configuration file parsing error `syntax error', stopped at line 16.

Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0xb7c8d82c>> ignored
Terminated
tuan@tuan:~/Desktop/weatherforecast-0.2.0$ 
Can somebody show me how to fix it
[/PHP]

---

### Post by SOULRiDER on 2008-03-19
The program is crashing due to bad coding, unless you know how to program and can fix it youself or some other user fixed it, theres not much you can do yet :(

---

