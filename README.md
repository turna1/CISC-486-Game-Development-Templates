# 🎮 Naughty Baby

## 📌 Overview
Naughty Baby is a 3D survival and puzzle game where a mischievous baby keeps throwing objects while attempting risky antics. The babysitter must keep the baby safe, catch thrown items, and neutralize hazards like the diaper bomb. The design highlights physics interactions and finite state machines, aligning with course topics.

## 🕹️ Core Gameplay
Players control the babysitter and try to prevent chaos.  
Catch thrown toys to avoid mess and damage.  
Disarm or dispose of the diaper bomb before the timer ends.  
Win by keeping the safety meter above zero until the round timer ends.  
Lose if the safety meter reaches zero or the diaper bomb detonates.

## 🎯 Game Type
Survival and Puzzle Adventure

## 👥 Player Setup
Single player as the babysitter  
Optional local co-op where a second player controls the baby for testing

## 🤖 AI Design
### Baby FSM
Idle  
Explore target of interest  
Mischief prepare throw or reach danger zone  
Throw select object and launch with force  
Escape move toward off-limits area  
Soothing temporarily calmed after being picked up or after toy returns

### Throwable Object FSM
AtRest on surface or in container  
PickedUp parented to baby hand  
Thrown physics enabled and in flight  
Caught parented to babysitter hand  
Disposed placed in bin or safe zone  
HazardArmed only for diaper bomb type

## 🎬 Scripted Events
Toy chest event at 60 seconds that spawns a burst of toys with randomized mass and bounciness  
Power outage mini event that reduces light and raises difficulty for 15 seconds  
Diaper bomb spawns with a visible timer and beep cue

## 🌍 Environment
Interior house scene with living room, kitchen, and nursery  
NavMesh baked for AI pathing  
Interactive props with colliders such as doors, drawers, bins, outlet covers, baby gate

## 🧪 Physics Scope
Rigidbody on baby, babysitter, and throwables  
Colliders and triggers on hands, bins, hazards, and gates  
Physics materials for toys rubber ball high bounciness, blocks low bounciness  
Layer-based collision matrix hands catchable, world static, hazard  
Force-based throws calculated from baby arm animation and intent  
Catch window defined by trigger volume on babysitter hands with relative velocity threshold  
Simple ragdoll or joint-based flail for baby during Mischief if time permits

## 🧠 FSM Scope
State machines implemented for baby and throwable objects  
Event driven transitions using Unity events and C# events  
Timers for diaper bomb arming and detonation  
Blackboard style memory for baby last seen hazard, last seen babysitter, favorite toy  
Debug overlay that prints current states for grading

## 🧩 Systems and Mechanics
Scoring gain points for catches, lose points for misses, streak bonus for consecutive catches  
Safety meter decreases when hazards occur and replenishes slowly when calm  
Diaper bomb rules arm on spawn, can be caught and disposed into bin, detonates if timer expires or if it collides with stove zone  
Object tagging Toy, Hazard, Catchable, Bin, StoveZone  
Camera third person follow with collision handling  
Audio cues baby giggle when Mischief, rising beep for bomb, thud on missed catch  
VFX confetti on perfect catch, smoke puff on bomb disposal, stink cloud on bomb near detonation

## 🎮 Controls
W A S D move  
Mouse look  
Space jump  
E interact pick up, catch, drop, close door, disarm  
Q quick toss to nearest bin  
Esc pause

## 📂 Project Setup aligned to course topics
Unity (version)
C# scripts for PlayerController, BabyAIController, ThrowManager, CatchZone, BombController  
NavMesh for AI pathing  
Animator controllers for baby and babysitter with parameters speed, isHolding, isThrowing, isCalm  
Physics materials and layers configured in Project Settings  
GitHub Classroom repository with regular commits and meaningful messages  
Readme and in game debug UI showing FPS, state names, and safety meter for assessment
