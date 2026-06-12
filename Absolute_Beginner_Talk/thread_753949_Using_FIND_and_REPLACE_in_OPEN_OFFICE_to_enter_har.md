---
title: "Using FIND and REPLACE in OPEN OFFICE to enter hard return after periods..."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by emergingtechnologies on 2008-04-13
I'm used to using the FIND and REPLACE feature in word processors to replace PERIODS with  PERIOD HARD RETURN HARD RETURN --  

Example: FIND    .   REPLACE  . ^p^p


This works in my Old word processor but it is not working in Open Office word processor -- does anyone have any ideas?

---

### Post by Helgiks on 2008-04-13
Do you want to delete first two letters before every period?

In that case you can try using regular expressions, more options -> check regular expresions and searching for somthing like "..\." and replace it with a "."

The above wil look for any two letters ending with a period and replace them, i.e. delete them.

If this is not what you mean than please be more precise.

---

### Post by emergingtechnologies on 2008-04-13
Thanks for the reply, Helgiks.

More precisely -- I want to find all occurrences of

PERIOD followed by SPACE SPACE

Then I want to REPLACE those with

RETURN RETURN...

In MS Word there is a special characters menu in the find replace area that allows me to do this.  How is it done in Open Office?

Thanks,
Chris

---

### Post by erginemr on 2008-04-13
It remember having used **^p** and sometimes **^l **extensively in MS Word.

As **Helgiks **has suggested, you can do it via regular expressions in OOo. To find the full stops between sentences, and add two line feeds after each, you can do something like:

* Find Dialog -> More options -> Check regular expressions.

* Find -> **\. **(followed by a space if there are spaces after the full stops. And if you don't use the backslash, it will assume **any character** in regex, so \ which is called an escape character is necessary.)

* Replace -> **.\n\n**

This will have such an effect as in the attachment.

---

### Post by Rinzwind on 2008-04-13
Look for "regular expressions" in the OOo Help index:

List of Regular Expressions Character Result/Use Any character Represents the given character unless otherwise specified.
\n
Represents a line break that was inserted with the Shift+Enter key combination. To change a line break into a paragraph break, enter \n in the Search for and Replace with boxes, and then perform a search and replace.
\n in the Search for text box stands for a line break that was inserted with the Shift+Enter key combination.
\n in the Replace with text box stands for a paragraph break that can be entered with the Enter or Return key.

---

### Post by erginemr on 2008-04-13
I agree. Once you get the hang of regex's, you will find the other word processor's character matching scheme very limiting, compared to the power of regex.

---

### Post by Helgiks on 2008-04-13
> **erginemr said:**
> I agree. Once you get the hang of regex's, you will find the other word processor's character matching scheme very limiting, compared to the power of regex.

Yes, all hail the power of the regex.

---

