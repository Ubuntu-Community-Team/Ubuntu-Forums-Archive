---
title: "gpg public key"
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by ~J~ on 2005-10-12
Apologies if this is the wrong forum...

Just gone onto Gnome-Look to register and one on the details it's asked for is a "gpg public key".

I've seen this on a few Linux sites and was wondering what on earth it is!

TIA

---

### Post by swerner on 2005-10-12
GPG is a patent free method of encrypting and signing data.  I will explain what encryption and signing is for. Then explain how it works and why you need the public (and a private key)

Encryption: If you want to send a message to someone and you don't want anybody along the line to intercept your message you can encrypt the message using a cypher.  A simple cypher used by the Romans is to replace each letter with another, eg 'abcde...' becomes 'tsrqp...', such that the word 'bad' would encode to 'stq'.  This is a very simple cypher, with todays computers we can use much more complicated cyphers to encode messages.  The receiver can then decode the message if they know your cypher. And, hopefully, no one in the middle can read your message.

Digital signing is similar.  When you post something on the internet and you want to confirm it comes from you, you sign it, using your GPG signature.  This signature is a series of alpha-numeric values.  It requires your public key to encode the signature.

The Keys:  There are two keys involved with digital encryption and digital signing.  One is your private key, you keep this one locked away as well as you can.  The other is your public key, you can give this freely to anyone any they can then verify that you digitally signed your post on the internet.  Or they will be able to use it to decode your encrypted message.  These two keys are mathematically related, it's complicated, do ask me exactly how.  Key creation and the encryption process rely on a method called factorisation, basically this means something that is computation easily done one way (encoding), but not the other (decoding without the private key).  This means that you can quickly and easily encode a message using your public and private keys, by only knowning the private key of the receiver.  And the message will only be veiwable by the receiver.  Someone who intercepts the message will have a _very_ difficult time decoding the message if they don't know the private key of the receiver.  _Very_ difficult means that it would take an ordinary computer the life of the universe (billions of years) to decode the message.  Although quantum computer, if and when they become available, will be able to do this in a very short length of time.

Similarily for a GPG signature, you can quickly sign the post using your public and private keys.  The by providing your public key others can quickly see that it was you who wrote it. Again it is _very_ difficult (but not impossible) to fake the GPG signature.  

I hope this answers your question.  Digital encryption is an interesting subject and there is lots about it on the internet.  There are also projects that try and break digital encryption.  To date no one has come up with a method to quickly decode a message without the private key, and it looks like it's going to be a solid form of encryption, at least until quantum computers scale.

---

### Post by ~J~ on 2005-10-12
What a fantastic reply!

Thanks for that swerner, much appreciated.

---

### Post by thespinesplitter on 2005-10-12
gotta give you props too

---

### Post by ds[de] on 2005-10-12
[QUOTE=swerner]This means that you can quickly and easily encode a message using your public and private keys, **by only knowning the private key of the receiver.**[/QUOTE]

I might be wrong here, but didn't you mean to write "(...) by only knowing the public key of the receiver:", since no-one besides the owner of the private key is supposed to know it.

If it's anything like PGP (which I assume it is), you create a pair of keys, a public key and a private key. The public key is used to encrypt messages. These messages can only be decrypted by the private key that was created along with the public key.
So if someone wants to keep the information for you secure from others, he would encrypt his message with your (the receiver's) public key, thus only allowing you to decrypt the message and vice versa. The sender doesn't need to know your private key to encrypt something.

I think that's basically what swerner was saying but I can't help but thinking he mixed something up (no offense of course, nice post).

Regards, 
ds[de]

---

### Post by thespinesplitter on 2005-10-12
so would you consider having one as necessary, i have a shell with webspace i could use to put mine, but i really havent needed one yet

---

### Post by swerner on 2005-10-12
Doh.  Yip I meant to say Public.  I'd better make sure I don't make mistakes like "yeah you can upload your PUBLIC key ;)"

---

