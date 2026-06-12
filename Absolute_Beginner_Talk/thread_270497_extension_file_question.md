---
title: "extension file question"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-03
i modified my extension file to look like this: 
type/^PDF
        Open= kpdf %f
        #Open=run-mailcap application/pdf:%f &
        #Open=(xpdf %f &)
        #Open=(acroread %f &)
        #Open=(ghostview %f &)
        View=%view{ascii} kpdf %f -  
concerning opening pdf files and problem is i get an error message which looks like this:
 Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
Error (594868): Unterminated string
Error (594874): Dictionary key must be a name object
Error (594878): Dictionary key must be a name object
Error (594885): Dictionary key must be a name object
Error (594894): Dictionary key must be a name object
Error (594897): Dictionary key must be a name object
Error (594909): Dictionary key must be a name object
Error (594913): Dictionary key must be a name object
Error (594917): Dictionary key must be a name object
Error (594919): Dictionary key must be a name object
Error (594971): Dictionary key must be a name object
Error (594977): Dictionary key must be a name object

 but still, the files open with kpdf. what is the solution for not having those error messages?

---

