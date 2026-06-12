---
title: "Spill the WINE"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-02-02
Still trying to get WINE to work.  When I type "wine cfg" from the konsole prompt I get:

> fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
Warning: the specified Windows directory L"c:\\windows" is not accessible.
fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
fixme:ntdll:FILE_GetNtStatus Converting errno 40 to STATUS_UNSUCCESSFUL
wine: cannot open (null)


What should be my next step? (besides electroshock treatment)

---

### Post by Kimm on 2006-02-02
it should be one word "winecfg", try that :)

---

### Post by Cousindaddy on 2006-02-02
Still get the same result...

---

### Post by iansyngin on 2006-02-02
what about sudo winecfg

---

### Post by Cousindaddy on 2006-02-02
Thanks...solved the problem a different way....  When I want to run a Windows program I simply boot XP...I find this solution saves the most time...

---

