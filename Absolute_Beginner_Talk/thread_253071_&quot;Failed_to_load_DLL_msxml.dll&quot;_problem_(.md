---
title: "&quot;Failed to load DLL msxml.dll&quot; problem (Wine)"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by lain1138 on 2006-09-07
hello!

I read one HowTo on S1MP3 wiki about avi to amv conversion and i'am stuck on on first step:

> You will first need msxml.dll, quartz.dll and qedit.dll (google for the files and copy to ~/.wine/drive_c/windows/system32) and run regsvr32 msxml.dll && regsvr32 qedit.dll. If msxml.dll fails to register, you need a different version (the one that depends on msxmlr.dll can't be used).

I downloaded dlls and cp-ed them to system32 directory
then i tryed to run [B]regsvr32 msxml.dll && regsvr32 qedit.dll
[/B]
but the terminal answered "Failed to load DLL msxml.dll"

then i downloaded other versions of msxml.dll, replaced them with current version but with no result.

can someone please help me?

thanks

---

### Post by johnbl on 2006-09-19
Did you get any direct responses to your question?

I as you seem to have a problem with msxml.dll. Downloaded ex MS site. File is in capitals so ran;


 regsvr32 MSXML.DLL && regsvr32 qedit.dll
with this result.

Failed to load DLL MSXML.DLL

Looks exactly as your situation is /was.

Any ideas out there?

Cheers

John

---

