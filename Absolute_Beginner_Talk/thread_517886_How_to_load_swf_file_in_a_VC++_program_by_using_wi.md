---
title: "How to load swf file in a VC++ program by using wine"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by niule on 2007-08-05
I've got a program writing in Visual C++... It loads a swf file by "shockwave flash object" and it's ok on Windows OS.

Now I have to execute the program under Ubuntu.

First of all , I copy the MFC dll files to the wine system,so the program could run now.

After that ,I registered the file "flash9.ocx", and installed the "firefox" and activeX file for it.

but still I got the errors following:

err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered 
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x1 
err:ole:ITypeInfo_fnInvoke did not find member id 191, flags 0x8! 
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE 

Meanwhile, I could see the flash player by Right click,but fail in loading the swf file..

Pls tell me how to fix this? Is there any missing rigistered file so sth else?

Regards

---

### Post by PriceChild on 2007-08-05
*move and bump*

btw linux has not shockwave client.

---

### Post by niule on 2007-08-07
i'm running the program under wiine,

so it will run as a program under windows,

regards

---

