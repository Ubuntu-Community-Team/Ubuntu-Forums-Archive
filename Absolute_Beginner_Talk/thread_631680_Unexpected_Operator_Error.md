---
title: "Unexpected Operator Error"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by sllorca on 2007-12-04
I was trying to install a dedicated server for battlefield 1942. It is a .run extension and I can run it and get through the EULA and then it says "type accept or decline" (for the terms of the eula) and so I type "accept" and the error it gives me is "[:  19:  ==:  unexpected operator" It does this for 2 lines and then waits for a command. It gives me the same error when I run it logged in as root. Anyone have any ideas what it could be?

---

### Post by PeterJS on 2007-12-04
> **sllorca said:**
> I was trying to install a dedicated server for battlefield 1942. It is a .run extension and I can run it and get through the EULA and then it says "type accept or decline" (for the terms of the eula) and so I type "accept" and the error it gives me is "[:  19:  ==:  unexpected operator" It does this for 2 lines and then waits for a command. It gives me the same error when I run it logged in as root. Anyone have any ideas what it could be?


I can't say for certainty with out looking at the installer itself, but based on the error it gave it looks like the installer is actually a shell script, shame on them for not using the standard .sh extension. Further more looks like it's a bug in their script, based on the (technically) incorrect but usually safe assumption that /bin/sh is just an alias of bash, Ubuntu is one of two distributions (ubuntu and debian) that use the more sh compliant dash by default. You could edit the first line from:
```

#!/bin/sh

```to
```

#/bin/bash

```or you could explicitly invoke the script with bash as follows:
```

bash ./installer_name.run

```

---

