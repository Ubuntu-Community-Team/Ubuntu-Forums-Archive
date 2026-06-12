---
title: "Seek help making dual boot Mac Mini 1,1 system, with cross permissions."
date: 2016-08-27
forum: Apple Hardware Users
---

### Post by lukon on 2016-08-27
In my attempt to make a my Mac Mini 1,1 dual boot OSX 10.5 and Ubuntu 14.04, I have set things up incorrectly pertaining to sharing drive space between these OS's. And I don't know how to fix it.

My goal is to have the single hard drive divided into partitions for each OS, and another one for files that can be accessed from either OS.

I encountered the user ID mismatch problem and tried to fix it by assigning the Ubuntu user ID to 501, to match that of the OSX 10.5 user ID. I did so by trying to follow the instructions I found on this web page: [http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems](http://lifehacker.com/5702815/the-complete-guide-to-sharing-your-data-across-multiple-operating-systems)

That procedure had me create a “tempuser” account in Ubuntu. Then us some chown commands on the home directory of Ubuntu. I guess that worked. But of course, I also wanted to do the chown command on my shared files partition. This gave me errors about permissions and stuff that I didn't understand.

Now I can't even access USB pen drives for lack of permissions.

Anyway, after giving up all this for awhile, I have yet to delete the “tempuser” account.

But now it seems the “tempuser” account is the only account there is. I “lost” the regular user account – don't know how to log into it.

So, I'd like some guidance on how to get all this sorted out.

---

