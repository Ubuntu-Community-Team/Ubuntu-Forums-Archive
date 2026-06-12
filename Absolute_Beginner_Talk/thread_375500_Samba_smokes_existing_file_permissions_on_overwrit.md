---
title: "Samba smokes existing file permissions on overwrite"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by iconridge on 2007-03-03
Hi, this is probably a samba question, but I drank ubuntu kool aid last night and this weirdness is not typical of other samba installs I've done, so thought it might be deb-untu specific...

Last night installed dapper drake on my dev server. OT: Kudos, my dev server is an obsolete 6U Compaq with highly bizarre hardware conf, and install went pretty clean. 

Post install everything's great, once I got used to the quirks in apache conf, etc, and found out that default install doesn't include typical things like um, gcc, make, etc, and got that humming, everything went pretty smoothly.

Here's the deal. When I open a file on the dev server, using drive mappings thru samba, edit that file, and save it, the file's original permissions get smoked and set back to samba default mask for new files. Example for given file index.cgi:

-rwxr-xr-x 1 aaron aaron  748 2007-03-03 17:30 index.cgi

Permissions are 755, as intended, after chmod'ing. Now, open that file thru samba drive mapping, edit it on my laptop, and resave it...

-rwxr--r-- 1 aaron aaron  750 2007-03-03 17:53 index.cgi

Execute bits are stripped when resaved. This is atypical, based on my prior use of samba on different platforms but I am certainly no samba expert. Is there a samba config param that will allow an overwrite to retain the original file permissions?

Thanks,
Aaron

---

### Post by jpkotta on 2007-03-03
I think the correct parameter is "security mask".
> security mask (S)

This parameter controls what UNIX permission bits can be modified when a Windows NT client is manipulating the UNIX permission on a file using the native NT security dialog box. 

This parameter is applied as a mask (AND'ed with) to the changed permission bits, thus preventing any bits not in this mask from being modified. Make sure not to mix up this parameter with force security mode, which works in a manner similar to this one but uses a logical OR instead of an AND. 

Essentially, zero bits in this mask may be treated as a set of bits the user is not allowed to change. 

If not set explicitly this parameter is 0777, allowing a user to modify all the user/group/world permissions on a file. 

Note that users who can access the Samba server through other means can easily bypass this restriction, so it is primarily useful for standalone "appliance" systems. Administrators of most normal systems will probably want to leave it set to 0777. 

Default: security mask = 0777 

Example: security mask = 0770
There is a corresponding mask for directories too.

Also, I had trouble with keeping permissions straight when I mapped shares with smbfs, but I've had much better luck with cifs.  cifs seems to work just like a local Linux filesystem, except it occasionally chokes on wierd characters in filenames (like accented/umlauted/etc. letters).

---

