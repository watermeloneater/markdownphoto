# PWM调制程序小问题--Voffset2为什么要乘以电流
## 问题回顾
1.在计算Voffset2的时候，当向量在1，2，3，4小扇区时，需要判断CHECKP和CHECKN
![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/%E5%A4%A7.PNG)

2.论文里关于这一块的详细判断方法如下
![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/%E8%AE%BA%E6%96%87.PNG)

3.DSP程序里面计算CHECKP和CHECKN的方法：
![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/%E7%A8%8B%E5%BA%8F.PNG)

### 问题：
    论文里面是直接比电压差值，而程序里面比的是电压差值乘以电流值
# 问题的解释
  论文里面最终是依靠向中点注入电流来调节中点电压的。
  计算得出需要注入的中点电流值如下：
  ![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/%E9%9C%80%E8%A6%81%E7%9A%84%E4%B8%AD%E7%82%B9%E7%94%B5%E6%B5%81%E8%AE%A1%E7%AE%97%E5%80%BC.PNG)
  
  然后才用这个值算出需要注入的中点电压Voffset2
  ![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/%E5%A4%A7%E5%85%AC%E5%BC%8F.PNG)
  
  已知条件为：
  
  ![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/%E4%B8%A4%E4%B8%AA%E5%B7%B2%E7%9F%A5%E7%9A%84%E5%85%AC%E5%BC%8F.PNG)

  经过化简可得：
  
  ![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/%E5%85%AC%E5%BC%8F.PNG)
  
  当s等于1时可得：
  
  ![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/s%3D1.PNG)
  
  当s等于-1时可得：
  
  ![Aaron Swartz](https://github.com/watermeloneater/markdownphoto/raw/master/s%3D-1.PNG)
  

>由此见得

    Voffset2乘以相应电流值所得数的大小才时最终影响输入中点电流的量度，程序的做法是有道理的。
    

