# Eternally Pwned: Exfiltration
#### Category: Forensics
![Screenshot from 2024-03-24 22-56-23.png](https://github.com/sudojacob/wolvctf24-writeup/blob/main/Screenshot%20from%202024-03-24%2022-56-23.png?raw=true)

##### The attached file is a .pcap, so we can analyze it using wireshark.

![image](https://github.com/sudojacob/wolvctf24-writeup/blob/main/Pasted%20image%2020240405223449.png?raw=true)

##### To get a nice summary of the traffic we look at `Statistics > Protocol Hierarchy`
![image](https://github.com/sudojacob/wolvctf24-writeup/blob/main/Pasted%20image%2020240405223636.png?raw=true)
![image](https://github.com/sudojacob/wolvctf24-writeup/blob/main/Pasted%20image%2020240405224247.png?raw=true)

##### Hmm... file sharing. Could find some secrets there!
##### We'll filter for only smb traffic.

![image](https://github.com/sudojacob/wolvctf24-writeup/blob/main/Pasted%20image%2020240405224359.png?raw=true)

##### That's a much more managable number of packets.

##### Clicking through each packet we see an interesting base64 looking string.

![image](https://github.com/sudojacob/wolvctf24-writeup/blob/main/Screenshot%20from%202024-04-05%2022-48-33.png?raw=true)

##### Decoding this we get the following: `wctf{l3tS_`
##### Definitely seems promising! Now to find the rest of it...

##### We can click on that packet and follow the TCP stream to find more.

![image](https://github.com/sudojacob/wolvctf24-writeup/blob/main/Pasted%20image%2020240405230325.png?raw=true)
![image](https://github.com/sudojacob/wolvctf24-writeup/blob/main/Pasted%20image%2020240405230036.png?raw=true)

##### By scrolling through the stream we can find two more pieces of base64.
##### Decoding these we get ```3teRn4lLy_g0_``` and ```bLU3_7n9wm4iWnL}```

##### We can combine these parts to get the full flag:
##### `wctf{l3tS_3teRn4lLy_g0_bLU3_7n9wm4iWnL}`
