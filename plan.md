# Streamlined Learning Agent System Plan

## Overview

This plan outlines a streamlined learning agent system designed to enhance education in programming and academic subjects. Based on multi-agent system best practices, we've consolidated roles into 3 agents (2 primary, 1 subagent) to minimize complexity while supporting all learning styles (interactive quizzes, explanations, projects, spaced repetition), multiple formats (conversational tutoring, structured lessons, Q&A), and addressing core challenges (concept understanding, practice, progress tracking).

## Data Storage

- **User Learning Data**: Stored in `user_learning_data.json` in project root
- **Learning Materials**: Organized in `learning_materials/{course}/{session}/` folders
- **Agent Configurations**: Located in `.opencode/agent/` directory

## Learning Agent System Architecture

### Primary Agents (Direct User Interaction)

**1. Learning Coordinator**

- **Role**: Main orchestrator for personalized learning journeys
- **Capabilities**:
  - Conduct initial assessments (background, goals, learning style)
  - Design adaptive curricula and learning paths
  - Coordinate with other agents and manage sessions
  - Provide motivation, feedback, and progress summaries
- **Mode**: Primary agent with full tool access
- **OpenCode Config**: Existing `learning-coordinator.md` with enhanced delegation logic

**2. Subject Specialist**

- **Role**: Deep-dive expert for specific programming/academic subjects
- **Capabilities**:
  - Deliver subject-specific content, explanations, and examples
  - Generate quizzes, practice problems, and adaptive assessments
  - Adapt difficulty based on learner performance
- **Mode**: Primary agent (allows direct switching with Tab key for focused sessions)
- **OpenCode Config**: New `subject-specialist.md` with teaching-focused tools

### Subagents (Invoked by Primary Agents)

**1. Learning Support**

- **Role**: Assistant for resources, projects, and long-term progress
- **Capabilities**:
  - Curate external resources (tutorials, documentation, videos)
  - Generate interactive projects with milestones
  - Track overall progress, implement spaced repetition, and analyze feedback
  - Detect learning styles and optimize approaches
- **Mode**: Subagent (invoked via @learning-support)
- **OpenCode Config**: New `learning-support.md` with read-only, support-focused tools

## Implementation Plan

### Phase 1: Agent Configuration (Core Infrastructure)

- **Refine learning-coordinator.md**: Enhance orchestration for @subject-specialist and @learning-support delegation
- **Create subject-specialist.md**: Primary agent for subject teaching with balanced tools/permissions
- **Create learning-support.md**: Subagent for supplementary learning tasks with restrictive permissions

### Phase 2: Integration & Testing (Interactive Learning Tools)

- Implement session navigation and context sharing between agents
- Add multi-modal support (text, code, diagrams) via webfetch and code tools
- Test agent switching (Tab for primary), @ invocations, and handoffs

### Phase 3: Advanced Features & Polish

- Optimize performance and user experience
- Add visual learning aids and concept mapping
- Implement feedback analysis for personalization

## User Interaction Flow

1. **Initial Assessment**: Coordinator evaluates user background and goals
2. **Personalized Learning Path**: Designs curriculum with milestones
3. **Dynamic Sessions**: Users engage in:
   - Conversational tutoring (Coordinator/Subject Specialist)
   - Structured lessons with quizzes (Subject Specialist)
   - Hands-on projects (Learning Support)
   - Review sessions (Learning Support)
4. **Progress Monitoring**: Continuous tracking with adaptive adjustments
5. **Agent Coordination**: Seamless switching via Tab or @ mentions

## Technical Considerations

- **Streamlined Architecture**: 3 agents minimize overhead while maintaining specialization
- **OpenCode Integration**: Uses Markdown agent configs with YAML frontmatter, tools, and permissions
- **Adaptive Learning Engine**: Performance data drives difficulty and approach adjustments
- **Multi-Subject Support**: Extensible for new domains via prompt updates
- **Privacy-Focused**: All data local; no external tracking
- **Tool Integration**: Leverages OpenCode's file editing, terminal, and web tools

## Agent Configuration Details

All agents configured in `.opencode/agent/` as `.md` files with:

- **Frontmatter**: mode, description, model, temperature, tools, permissions
- **Prompt**: Detailed system prompt defining role and capabilities
- **Delegation**: Coordinator invokes subagents via @ mentions for modular execution

