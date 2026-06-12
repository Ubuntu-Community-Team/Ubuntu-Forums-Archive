---
title: "Suggestions - upgrade nullmailer + provide basic MTA wizard"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by mikeorb on 2006-01-09
Don't really see a feedback forum/system, so here goes. My ISP (SBC DSL) blocks port 25 and my e-mail/etc. provider (Dreamhost) requires outbound SMTP authentication. All very typical these days. Anyway, AFAIKT postfix does not support this and is really overkill anyway if you just want to get /usr/lib/sendmail to send to an upstream mail server and possibly run an SMTP relay server locally behind your firewall for apps that want to talk directly SMTP.

But nullmailer 1.01 does support this. Unfortunately the version on the repositories used by my Synaptic install lists 1.00RC7. So my suggestion is to upgrade to the latest (I'll just install myself).

But a larger suggestion is to add a mail MTA setup wizard or some such to the install process and to the Admin taskbar. Something to guide the user through basic setup, perhaps configuring either nullmailer or postfix depending on the user's needs. I had to dig for awhile to find nullmailer as a good solution and this seems like a common need. Then again, I may have missed this in my original install and just forgot :-(.

Regards,
-Mike

---

### Post by mikeorb on 2006-01-09
FYI to anyone using nullmailer 1.01. This patch needs to be applied to fix a bug in SMTP authentication:

--- protocols/smtp.cc	(revision 142)
+++ protocols/smtp.cc	(working copy)
@@ -147,7 +147,11 @@
 
   if (user != 0 && pass != 0)
   {
-    mystring plain = mystring(user) + '\0' + user + '\0' + pass;
+    mystring plain(user);
+    plain += '\0';
+    plain += user;
+    plain += '\0';
+    plain += pass;
     mystring encoded = "AUTH PLAIN ";
     base64_encode(plain, encoded);
     conn.docmd(encoded, 200);

---

