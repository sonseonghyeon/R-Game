# R-Game
R 게임 프로젝트 -2019.5.2~-
# game intro
Game <- function() {
  ANSWER <- readline("Do you want to start the game?")
  if (ANSWER == "OK")
    print("Game Start!")
  else
    print("Unable to start game")
}

if(interactive()) Game()
# order a game

a <- c("rock", "scissors", "paper")
student1<- sample(a, 1, replace = T)
student2<- sample(a, 1, replace = T)
if(student1 == "rock" & student2 == "rock"){
  print("tie. Try again!")
  user1<-"NaN"
  user2<-"NaN"
}else if(student1 == "rock" & student2 == "scissors"){
  print("Student1 win, student2 loss")
  user1 <- c("student1")
  user2 <- c("student2")
}else if(student1 == "rock" & student2 == "paper"){
  print("Student1 loss student2 win")
  user2 <- c("student1")
  user1 <- c("student2")
}else if(student1 == "paper" & student2 == "paper"){
  print("tie. Try again")
  user1<-"NaN"
  user2<-"NaN"
}else if(student1 == "paper" & student2 == "scissors"){
  print("Student1 loss student2 win")
  user1 <- c("student2")
  user2 <- c("student1")
}else if(student1 == "paper" & student2 == "rock"){
  print("Student1 win student2 loss")
  user2 <- c("student2")
  user1 <- c("student1")
}else if(student1 == "scissors" & student2 == "scissors"){
  print("tie. Try again")
  user1<-"NaN"
  user2<-"NaN"
}else if(student1 == "scissors" & student2 == "rock"){
  print("Student1 loss student2 win")
  user2 <- c("student1")
  user1 <- c("student2")
}else if(student1 == "scissors" & student2 == "paper"){
  print("Student1 win student2 loss")
  user1 <- c("student1")
  user2 <- c("student2")
}

user1
user2

number <- c(1:25)

# set.seed(0) 빙고판 고정용 (새로운 게임 원할 시 제외시킨다)
bf <- sample(number,size = 25,replace = F)
user1 <- matrix(data=bf,nrow = 5)
(user1 <- as.data.frame(user1))
bf2 <- sample(number,size = 25,replace = F)
user2 <- matrix(data=bf2,nrow = 5)
(user2 <- as.data.frame(user2))
user1
user2


A <- readline('insert plseas : ')
if((which(A==user1) %% 5) == 0){
  x <- 5
} else {
  x <- which(A==user1) %% 5
}
if((which(A==user1) %% 5) == 0){
  y <- which(A==user1) %/% 5
} else {
  y <- (which(A==user1) %/% 5) + 1
}
user1[x,y] <- 0
if((which(A==user2) %% 5) == 0){
  x <- 5
} else {
  x <- which(A==user2) %% 5
}

if((which(A==user2) %% 5) == 0){
  y <- which(A==user2) %/% 5
} else {
  y <- (which(A==user2) %/% 5) + 1
}
user2[x,y] <- 0

user1
user2

#user1 세로합
a <- c(sum(user1$V1)==0,sum(user1$V2)==0,sum(user1$V3)==0,sum(user1$V4)==0,sum(user1$V5)==0)
#user1 가로합
b <- c(sum(user1[1, ])==0,sum(user1[2, ])==0,sum(user1[3, ])==0,sum(user1[4, ])==0,sum(user1[5, ])==0)
#user1 대각선합
c <- c(sum(user1[1,1]+user1[2,2]+user1[3,3]+user1[4,4]+user1[5,5])==0,sum(user1[1,5]+user1[2,4]+user1[3,3]+user1[4,2]+user1[5,1])==0)

user1_bingo <- if(sum(c(a,b,c))==1){
  print("한줄빙고")
} else if(sum(c(a,b,c))==2){
  print("두줄빙고")
} else if(sum(c(a,b,c))==3){
  print("세줄빙고")
} else if (sum(c(a,b,c))==0){
  print("빙고없음")
}


#user2 세로합
aa <- c(sum(user2$V1)==0,sum(user2$V2)==0,sum(user2$V3)==0,sum(user2$V4)==0,sum(user2$V5)==0)
#user2 가로합
bb <- c(sum(user2[1, ])==0,sum(user2[2, ])==0,sum(user2[3, ])==0,sum(user2[4, ])==0,sum(user2[5, ])==0)
#user2 대각선합
cc <- c(sum(user2[1,1]+user2[2,2]+user2[3,3]+user2[4,4]+user2[5,5])==0,sum(user2[1,5]+user2[2,4]+user2[3,3]+user2[4,2]+user2[5,1])==0)

user2_bingo <- if(sum(c(aa,bb,cc))==1){
  print("한줄빙고")
} else if(sum(c(aa,bb,cc))==2){
  print("두줄빙고")
} else if(sum(c(aa,bb,cc))==3){
  print("세줄빙고")
} else if (sum(c(aa,bb,cc))==0){
  print("빙고없음")
}

if(user1_bingo=="세줄빙고"){
  print("user1의 승으로 빙고게임이 끝났습니다.")
} else if(user2_bingo=="세줄빙고"){
  print("user2의 승으로 빙고게임이 끝났습니다.")
}
