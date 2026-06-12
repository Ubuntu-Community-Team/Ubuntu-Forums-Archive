---
title: "VMWare Help"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by djearwig on 2007-03-27
So I'm trying to virtualize my Ubuntu 6.1 server with VMware.  I downloaded the tarball, extracted it, ran it, and configured it with no problem until the end.  It asks for a serial number and I enter the one supplied (all caps with hyphens intact) and I get an error that the serial is invalid.  
And I get an error that it couldn't open libXt.so.6 (no such directory or file).  I also got an error that the vmware-vmx file couldn't be read,or something.  I checked that out and discover it has been converted from DOS and Mac format and that it shows up highlighted in red when I do an 'ls' on the folder: eric@ubuntu-server:/usr/lib/vmware/bin$.  I nano the file and it look like this:  ^?ELF^A^A^A^@^@^@^@^@^@^@^@^@^B^@^C^@^A^@^@^@ï¿½Ý^D^H4^@^@^@Üï¿½B^@^@^@^@^@4^@ ^^A^@^@^@^@^@^@ï¿½^A^@^@^@^@^@^@^@^@^@^@?^@^@^@ï¿½^@^@^@w^@^@^@ï¿½^@^@^@^S^A^@^@ï^@^@^@^@^@^@^@^N^@^@^@^S^@^@^@^V^@^@^@^Z^@^@^@^D^@^@^@^@^@^@^@,^@^@^@^@^@^@^@^@$
^@^@^@Z^A^@^@@^A^@^@e^A^@^@6^A^@^@ï¿½^@^@^@
^A^@^@&^A^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@y^D^@^@^@^@^@^@ï¿½^^@^@^@^@^@^@:^@^@^@^R^@^@^@j
^@^@^@^@^@^@}^A^@^@^R^@^@^@^O^K^@^@^@^@^@^@ï¿½^@^@^@^R^@^@^@ï¿½^H^@^@^@^@^@^@ï¿½^@^@^@^@^@^@;^@^@^@^R^@^@^@=^C^@^@^@^@^@^@ï¿½^A^@^@^R^@^@^@Z^G^@^@^@^@^@^@z^@^@^^@^@^@^@^@^@T^@^@^@^R^@^@^@"^K^@^@^@^@^@^@ï¿½^C^@^@^R^@^@^@4^F^@^@^@^@^@^@U^@^@^^@^@^@^@^@^@ï¿½^@^@^@^R^@^@^@ï¿½^@^@^@^@^@^@^@a^@^@^@^R^@^@^@ï¿½
^@^@^@^@^@^@>^@^@^@^R^@^@^@1^B^@^@^@^@^@^@:^@^@^@^R^@^@^@^O^@^@^@^@^@^@^@ï¿½^@^@^@^@^@^@^@^@!^B^@^@^R^@^@^@u^P^@^@^@^@^@^@-^@^@^@^R^@^@^@^Y^A^@^@^@^@^@^@ï¿½^@^@^@^@^@^@^@^@^@^A^@^@^R^@^@^@5
^@^@^@^@^@^@I^@^@^@^R^@^@^@ï¿½^D^@^@^@^@^@^@k^A^@^@^R^@^@^@ï¿½^H^@^@^@^@^@^@^W^B^@^@^@^@^@^@ï¿½^@^@^@^R^@^@^@^G^E^@^@^@^@^@^@ï¿½^A^@^@^R^@^@^@ï¿½
^@^@^@^@^@^@1^@^@^@^R^@^@^@V^P^@^@^@^@^@^@ï¿½^@^@^@^R^@^@^@_^P^@^@^@^@^@^@G^A^@^^@^@^R^@^@^@x^F^@^@^@^@^@^@&^A^@^@^R^@^@^@ï¿½^P^@^@^@^@^@^@F^@^@^@^R^@^@^@ï¿½^B^^@^@^@^@^@^@ï¿½^@^@^@^R^@^@^@^H^O^@^@^@^@^@^@;^@^@^@^R^@^@^@ï¿½^A^@^@^@^@^@^@u^@^@ï¿½
            [ Read 18419 lines (Converted from DOS and Mac format) ]

Is this causing the error with my serial number?  I have a feeling it is trying to write the serial number to this file, but cannot.

Any suggestions...

Thanks

---

### Post by savastux on 2007-03-27
For start, you should contact your VMware vendor tell him that your license isn't valid.
Then, try again with the new license and see if the libXt.so.6 error occurs.
It might be an exception thrown by a misstyped license, who knows? 
Worth to try!


:c)


[]'s
Savastux

---

### Post by djearwig on 2007-03-27
OK  I'll start with your suggestion and contact VMWare and let them know the serials don't work.

Any ideas on why that vmware-vmx file looks so goofy?  I did port it over from a windows platform to Ubuntu using WinSCP, but I don't think that would corrupt the data...

?

---

### Post by djearwig on 2007-03-27
Just in case inquiring minds want to know:
I think the reason the vmware-vmc file looks so strange is because I used the 'zcat' command to move the file, but retain the original compressed file.
When I gunzipped the file and *then* copied it to a new location, it looked just fine.

---

### Post by djearwig on 2007-03-27
Nope, I jumped the gun - that was a problem with a different file...

The vmware-vmw file still looks as it does above.

so confused...

---

### Post by savastux on 2007-03-28
Well, looks like you've got a corrupted file.
Mine is in plain text. Can't you copy this file again?

If you are unsure that this file is being corrupted by WinSCP, or other programs that you have tried, why don't you e-mail it for yourself. As it has a tiny size. (mine is 2.2KB).

And let's how this works.
:c)

[]'s
Savastux

---

### Post by djearwig on 2007-03-28
OK Yeah, I think I'll try that...
After I finish configuring the server.  I'm putting LDAP on it and when I get done with that, then I'll worry about virtualizing and deploying this copy of the server over multiple virtual servers...

Thanks so much for the help; I really appreciate it!

---

