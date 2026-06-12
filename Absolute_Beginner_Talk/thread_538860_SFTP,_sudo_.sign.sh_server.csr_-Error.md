---
title: "SFTP, sudo ./sign.sh server.csr -Error"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by kbolio3 on 2007-08-30
Originally Posted by ikkinu  
1- Enable TLS/SSL encryption (FTPS) 
The FTP file sharing protocol is an old protocol which was created when internet was still a secure place, therefore the default FTP protocol is not that secure.
For example the password and username for login are transmitted in plain text which obviously isn't secure.
That why, to fit the needs of our generation, encryption solutions were developed and one of them is TLS/SSH encryption.
This will encrypt the username and password and all the data you send, obviously to use it the FTP client must support SFTP protocol.

here are the steps to enable TLS/SSH encryption (FTPS):

Paste these commands in a terminal :
Code:
sudo apt-get install build-essential
sudo apt-get install libssl-dev
cd /etc
sudo mkdir ftpcert
cd ftpcert/
sudo openssl genrsa -des3 -out server.key 1024
sudo openssl req -new -key server.key -out server.csr
sudo openssl genrsa -des3 -out ca.key 1024
sudo openssl req -new -x509 -days 365 -key ca.key -out ca.crt 
sudo wget [http://frodubuntu.free.fr/ubuntu/sign.sh](http://frodubuntu.free.fr/ubuntu/sign.sh)
sudo chmod +x sign.sh
sudo ./sign.sh server.csr


when I type sudo ./sign.sh server.csr I get this error:

CA signing: server.csr -> server.crt:
Using configuration from ca.config
Enter pass phrase for ./ca.key:
Check that the request matches the signature
Signature ok
The Subject's Distinguished Name is as follows
countryName :PRINTABLE:'IL'
stateOrProvinceName :PRINTABLE:'Ikkland'
localityName :PRINTABLE:'Ikktown'
organizationName :PRINTABLE:'Project ikkinu'
organizationalUnitName:PRINTABLE:'Ftp Dpt.'
commonName :PRINTABLE:'ikkinu'
emailAddress :IA5STRING:'ikkinu@inventati.org'
Certificate is to be certified until Dec 5 19:24:50 2007 GMT (365 days)
Sign the certificate? [y/n]:y


1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated
CA verifying: server.crt <-> CA cert
server.crt: /C=IL/ST=Ikkland/L=Ikktown/O=Project ikkinu/OU=Ftp Dpt./CN=ikkinu/emailAddress=xxx@xxx.xxx
error 18 at 0 depth lookup:self signed certificate
/C=IL/ST=Ikkland/L=Ikktown/O=Project ikkinu/OU=Ftp Dpt./CN=ikkinu/emailAddress=xxx@xxx.xxx
error 7 at 0 depth lookup:certificate signature failure
12603:error:04067084:rsa routines:RSA_EAY_PUBLIC_DECRYPT:data too large for modulus:rsa_eay.c:645:
12603:error:0D0C5006:asn1 encoding routines:ASN1_item_verify:EVP lib:a_verify.c:168:

Can anyone help me?
Thanks

---

### Post by llamakc on 2007-08-30
What is it you actually want to do: run a server or login to a server (with sftp)? 

Because "sftp" ships with the package openssh-client which is installed by default.

---

