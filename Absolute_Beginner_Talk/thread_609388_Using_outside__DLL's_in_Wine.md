---
title: "Using outside  DLL's in Wine"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by plr4ever on 2007-11-10
I keep hearing everywhere about using such and such dll's for Wine. I know where to get them, but i'm not quite sure if i need them. Are there some that will just make it run better, or is it a specific thing.

Also, would Microsoft Office 2003 work better if I used different DLL's/

---

### Post by scratched on 2007-11-11
Part of the Wine project is attempting to write DLLs that imitate Windows native DLLs. Sometimes, these DLLs are not as good as the originals. The reason you don't get the originals in Wine is because of licensing. Wine can't legally include these themselves because it could be illegal if you don't own windows. If you have a copy of Windows and you need a particular DLL, you can use the DLLs from Windows instead and there's a chance your software will work better (or just "work" in general).

I have no idea if Office 2003 will actually run any better with the native DLLs, but you could give it a shot. If you go to appdb.winehq.org you can search for Office 2003 to see if anyone has mentioned using other DLLs. I don't remember if it helps or not though...

---

