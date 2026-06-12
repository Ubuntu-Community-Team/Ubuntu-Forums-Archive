---
title: "TheLastRipper - rip to mp3 from &quot;Lastfm&quot; - needs change in Preferences.cs, &quot;mono&quot;"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-11-21
**where can I find the "Preferences.cs" file in Gutsy?**

has anyone managed to rip from Lastfm?

[http://code.google.com/p/thelastripper/issues/detail?id=70](http://code.google.com/p/thelastripper/issues/detail?id=70)

It seams some versions, probably newer versions, of mono doesn't support the old 1.1
method of changing proxy... Anyway, the solution is to comment out following lines in
Preferences.cs, that should make it compile, though proxy settings won't work:
//Use proxy if needed
if (this.ProxyServer != null && this.ProxyServer.Length > 0) {

	WebProxy iwp = new WebProxy(this.ProxyServer);

	if (this.ProxyUsername.Length > 0 || this.ProxyPassword.Length > 0) {

		iwp.Credentials = new NetworkCredential(this.ProxyUsername, this.ProxyPassword);

	}

	WebRequest.DefaultWebProxy = iwp;//TODO: reconsider this selections since it's
obsolete in .Net 2.0

} else {

	WebRequest.DefaultWebProxy = GlobalProxySelection.GetEmptyWebProxy ();

}


Just add /* at line 62, and */ at line 71

---

