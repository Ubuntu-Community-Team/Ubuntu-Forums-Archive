---
title: "GnuPG Signatures in Evolution and Thunderbird"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Alveric on 2006-12-19
If I write an email using Thunderbird and sign it with my GnuPG key using Enigmail, the email arrives in an Outlook mailbox with the whole email text gets a header-and-footer with the key details, clearly showing it is that text which has been signed.

If I write it using Evolution and sign with the same key, the email arrives with an attachment "signature.asc".

This may sound like a dumb question, but is there "best practice" for such things? Is it just that Outlook can't handle GnuPG signatures, and does it matter which way it appears?

Thanks for your opinion,

Al.

---

### Post by schwascore on 2006-12-19
I can't comment on the capabilities of Outlook, but every encrypted e-mail I have received has had the sig. in-line rather than as an attachment.  Of course this is just anecdotal evidence, I don't know what is the "official" best practice.

---

### Post by Alveric on 2006-12-20
> **schwascore said:**
>  ... every encrypted e-mail I have received has had the sig. in-line rather than as an attachment ... 

Thats what I thought - but Evolution just seems to attach the GnuPG signature as a file (.asc, which can be opened as a plain text file).

I did some googling and this shows up as a problem in the way Outlook (my receipient) handles such signatures, but I had a look in my googlemail sent items and even there the test email doesn't have "in-line" signing.

Has anyone else experienced this?

I may have to go back to Thunderbird/Enigmail for my email, because at least then it is clear that I _have _signed an email text!

Al.

---

