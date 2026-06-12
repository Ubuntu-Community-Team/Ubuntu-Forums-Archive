---
title: "MATLAB on MacBook Pro under Ubuntu"
date: 2009-11-22
forum: Apple Hardware Users
---

### Post by kmrjohnson on 2009-11-22
[B]cross-posted from science forum
[/B]             
                                                                I just bought a MacBook Pro running OS X 10.6 and have installed Ubuntu 9.10 under Parallels Desktop 5 in order to run MATLAB 2009b efficiently. MATLAB runs too slowly on the MacBook Pro under OS X 10.6, in fact no faster than on my old PowerBook G4. I am referring here to the speed of a specific piece of highly iterated numerical computation code from my particular project.

My question is: I'd like to use the MATLAB parallel computing toolbox and related functionalities to further speed up the computations. Will I be able to do this using Ubuntu via the Parallels Desktop? Is the computer going to be able to see the two Mac Minis I plan to connect to the main computer? Or am I better off booting the Mac up from a Linux disk (if this is possible)? Or some other approach? 

I'd appreciate hearing from someone who has tried to do something similar.

Thanks.

---

### Post by coolbreeze1 on 2010-01-25
This is code for parallel interference cancelltion in ds cdma using matrix algebraic approach.
Please check the code and let me know if iam doin any mistake . Also I need to apply slow and fast rayleigh fading in this model. 

The rcd signal is R = SAB + N 
where R,S,A,B are matrices 
The matlab code is given below : 
close all 
clear all; 
clc; 
warning off all 

K = 27; %No. of users 
Navg = 1e3; %No. of repititions 
snr = 5:1:25; %SNR RANGE 

Sv = (10.^(-snr/10)); %Noise variance in different SNR 
A = eye(K); %input power 
%Get signature sequences 
load GS31; 
S = GS31(1:K,; 
S= S'; 
Lc = length(S(:,1)); 
Sn= S./sqrt(Lc); %Normalize energy of signature waveforms 
R = Sn'*Sn; % Calculate correlation matrix 

corr=(R-eye(size(R))); 

h = waitbar(0,'WAIT...'); 
for t = 1:Navg 
waitbar(t/Navg); 
for j = 1:length(snr) 
noise =(Sv(j))^.5*randn(Lc,1); 
b=2*(randint(K,1)-0.5); 
BT=Sn*A*b; 
r=awgn(BT,snr(j)); 
% r=BT+noise; 
y = Sn'*r; 

ysdec = inv(R)*Sn'*r; 

YMF = sign(y); 
YDEC= sign(ysdec); 
novector(1:K) = Sv(j); 
sigma2= diag(novector); 

t1=R+sigma2; 
ysmmse = (inv ( t1 ))* y; 
YMMSE= sign(ysmmse); 

%%CPIC 

yinit=zeros(K,1); 
ypic1= (Sn'*r) + yinit ; 
YPIC1 = sign(ypic1); 

yinit2=ypic1; 
ypic2=(Sn'*r) - ( corr*A*yinit2 ); 
YPIC2 = sign(ypic2); 

yinit3=ypic2; 
ypic3=(Sn'*r) - ( corr*A*yinit3 ); 
YPIC3 = sign(ypic3); 


yinit4= ypic3; 
ypic4=(Sn'*r) - ( corr*A*yinit4 ); 
YPIC4 = sign(ypic4); 

yinit5= ypic4; 
ypic5=(Sn'*r) - ( corr*A*yinit5 ); 
YPIC5 = sign(ypic5); 


yinit6=ypic5; 
ypic6=(Sn'*r) - ( corr*A*yinit6 ); 
YPIC6 = sign(ypic6); 



yinit7=ypic6; 
ypic7=(Sn'*r) - ( corr*A*yinit7 ); 
YPIC7 = sign(ypic7); 


yinit8=ypic7; 
ypic8=(Sn'*r) - ( corr*A*yinit8 ); 
YPIC8 = sign(ypic8); 



ERMF(j)= length(find (YMF ~= b))/K; 
ERDEC(j)= length(find (YDEC ~= b))/K; 
ERMMSE(j)= length(find (YMMSE ~= b))/K; 
ERPIC1(j)= length(find (YPIC1 ~= b))/K; 
ERPIC2(j)= length(find (YPIC2 ~= b))/K; 
ERPIC3(j)= length(find (YPIC3 ~= b))/K; 
ERPIC4(j)= length(find (YPIC4 ~= b))/K; 
ERPIC5(j)= length(find (YPIC5 ~= b))/K; 
ERPIC6(j)= length(find (YPIC6 ~= b))/K; 
ERPIC7(j)= length(find (YPIC7 ~= b))/K; 
ERPIC8(j)= length(find (YPIC8 ~= b))/K; 
end 
EERMF(t,=ERMF; 
EERDEC(t,=ERDEC; 
EERMMSE(t,=ERMMSE; 
EERPIC1(t,=ERPIC1; 
EERPIC2(t,=ERPIC2; 
EERPIC3(t,=ERPIC3; 
EERPIC4(t,=ERPIC4; 
EERPIC5(t,=ERPIC5; 
EERPIC6(t,=ERPIC6; 
EERPIC7(t,=ERPIC7; 
EERPIC8(t,=ERPIC8; 
end 


BERMF = smooth(mean(EERMF,1)); 
BERDEC = smooth(mean(EERDEC,1)); 
BERMMSE = smooth(mean(EERMMSE,1)); 
BERPIC1 = smooth(mean(EERPIC1,1)); 
BERPIC2 = smooth(mean(EERPIC2,1)); 
BERPIC3 = smooth(mean(EERPIC3,1)); 
BERPIC4 = smooth(mean(EERPIC4,1)); 
BERPIC5 = smooth(mean(EERPIC5,1)); 
BERPIC6 = smooth(mean(EERPIC6,1)); 
BERPIC7 = smooth(mean(EERPIC7,1)); 
BERPIC8 = smooth(mean(EERPIC8,1)); 

semilogy(snr,BERMF,'k*-',snr,BERPIC1,'m^-',snr,BERPIC2,'rs-',snr,BERPIC3,'yo-',snr,BERPIC4,'k<-',snr,BERPIC5,'c^-',snr,BERPIC6,'y^-',snr,BERPIC7,'r>-',snr,BERPIC8,'bs-',snr,BERDEC,'g*-',snr,BERMMSE,'go-'); 
grid on 
xlabel('SNR') 
ylabel('Average BER') 
legend('MF','Stage1','Stage2','Stage3','Stage4','Stage5','Stage6','Stage7','Stage8','DECOR','MMSE') 
title('BER vs SNR--Conventional PIC-25 Users -AWGN Channel') 
close(h) 

Added after 1 minutes: 

Dear all, 

The : ) got replaced by a smiley. 

I need urgent help regarding fading 
thanks in advance

---

